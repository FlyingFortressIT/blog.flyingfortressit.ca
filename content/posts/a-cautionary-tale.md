---
title: "It's not all rainbows, but there's always a silver lining"
subtitle: Get it, cloud jokes?
date: 2017-08-13T14:03:48-05:00
author: Mike Himbeault
categories:
  - Cloud
  - AWS
  - Software maintenance
tags:
  - CloudFormation
  - S3
---

What follows is a brief tale of cloud adoption caution, and describes what happens when AWS makes something better, you don't update your code, and your builds start failing sometime in the future because of it.

<!--more-->

Today, one of our projects that uses [CloudFormation](https://aws.amazon.com/cloudformation/) (the AWS-specific infrastructure-as-code templating model for provisioning, configuring, and deploying AWS resources and code changes) started experiencing build failures. We had committed an update and deployed the updated code successfully yesterday, but today bringing up a new stack was failing. The template was unchanged, and no changes that were made indicated that this should be happening, so obviously we were puzzled. Code deploys don't test the same CloudFormation and deployment logic as a full fresh deploy, so there was a fair bit of surface that needed to be investigated.

My digging started with figuring out what was erroring. Our GitLab-CI pipeline just throws back the error from the boto3 waiter saying "Stack entered red state, deploy failed", so this required going and looking at the stack itself. Our deployments don't delete failed stacks so that this forensic log is retained. One thing they do, however, is roll back on failure, removing the resources that *did* successfully provision curing stack creation or update. Debugging this might have been a bit easier if they didn't roll back, but not not enough to matter.

We use CloudFormation Custom Resources implemented as Lambda functions inside of our template to handle some types of resources that CloudFormation does not currently support as first-class citizens. Specifically, the failed resource was a custom resource that managed S3 bucket lifecycle configurations (LCC) - which are partially supported when creating a bucket - that expire incomplete multipart uploads in the bucket. We use the same Lambda function (called with a different argument) to handle the creation and assignment of a CloudFront Origin Access Identity (OAI), which happens earlier in the stack creation than the S3 LCC.

Once I looked at the stack events log, I observed that the OAI created successfully, but the LCC did not. This told me that the Lambda function and execution environment was fine, so it was something about the LCC codepath. CloudFormation CustomResources that back on AWS Lambda have a physical ID that maps to a CloudWatch Logs log group where all output goes; heading over there I was treated to some Python logging output.

```
{'ErrorStr': "'Prefix'", 'ErrorDict': {}}
```

Wow. That's helpful, thanks Python.

If you've written Python, you've probably seen this one before. This specific function is pretty old, and hasn't been touched since very early in the project. All new error reporting also returns the `repr()` of the exception object attached to the `ErrorRepr` key, but this one doesn't. If we had included that, we'd have seen something nicer:

```
{'ErrorRepr': "KeyError('Prefix',)", 'ErrorStr': "'Prefix'", 'ErrorDict': {}}
```

So it's a `KeyError`. We're looking for `Prefix`, and it's not there. Specifically, we're looking for that in the return value of `get_bucket_lifecycle_configuration()`.

Initially I started taking a look at the boto and boto3 package commits on GitHub over the last month to see if there had been changes to the way default/empty parameters were handled for LCC related API calls. There was a bit of a red-herring here, as boto3 had just recently had several LCC changes committed. We aren't currently using a prefix (that is, the value is the empty string, indicating the LCC applies to the whole bucket), so I thought maybe empty strings were represented by a missing key? Checking the AWS API docs (and just looking at the Prefix parameter, not the rest...) shows it is *Optional*, so, maybe?

Twenty minutes of reading commit logs and testing previous boto3/botocore versions in an AmazonLinux Docker container, and nope, nothing. Definitely not the packages.

Heading over to the Boto3 [documentation for method in question](http://boto3.readthedocs.io/en/latest/reference/services/s3.html#S3.Client.get_bucket_lifecycle_configuration), and I notice something entertaining: there's two ways of specifying a Prefix filter on a LCC. There's the old way, with `Prefix` at the root, and then the new way that was made available when they added support for tag-based LCCs where it sits under a `Filter` key at the root.

Huh. This is ambiguous, and when we chose not to update our code with the API change, we implicitly made an assumption about how AWS services were going to choose to represent this going forward. This assumption was fine, until it was suddenly wrong.

The fix was simple, and a single-line change in the code, but it was a good illustration about how important developer diligence is. It is no longer safe to assume that API changes that are backwards compatible won't break your code or applications. Maintaining a strong relationship with your AWS account rep is important for staying on top of things like this, and making sure your developers are invested in maintaining older applications/packages, and backporting these fixes is vital for keeping things running.

Given this, the silver lining in is that I expect that CloudFormation will gain official support for the full feature-set of the new and improved S3 LCCs some time in the near future, which will be delightful.
