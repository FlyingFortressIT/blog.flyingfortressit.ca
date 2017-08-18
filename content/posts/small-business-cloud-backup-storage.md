---
title: "Small Business Cloud - Backup Storage"
date: 2017-08-17T09:09:34-05:00
author: Mike Himbeault
categories:
  - Cloud
  - Storage
  - Adoption
tags:
  - Backup
---

If you are a business, or even an individual, and you are starting to think about backup, there is a good chance you are going to consider cloud backup or storage providers. This article is intended to be a brief introduction on the how, when, and why to choose a provider, and why choosing a storage product is a bigger question than it seems.

At the end of this article, you will have a better idea of how your choice of storage provider factors into future cloud services adoption, and how to choose one that fits your needs.

<!--more-->

## The problems: Where, What, If

Cloud backup is often referred to as the gateway drug to additional cloud services adoption, and the reason for this is complicated but boils down to one thing: you are choosing more than just storage, you are choosing an _ecosystem_. In your on-premise environments, storage underpins every activity, procedure, or service that is a part of your business, and this is no different in a cloud environment.

In short: data has to live somewhere, and **where** it lives determines **what** you can do with it.

In your on-premise environment, the "where" is often determined by which storage appliance/disk-set the data resides on. Similarly, the "what" is typically determined by the applications installed on workstations or servers, and is limited by the performance of the "where".

In a cloud environment, however, the "where" is a mix of which provider (AWS, BackBlaze, rsync.net, etc...), and which product (AWS S3, BackBlaze B2, rsync.net ZFS, etc...) your data is stored using. The "what", however, is limited by the retrieval mechanisms and _pricing models_ the "where" supports. When data is stored on-premise, it costs nothing (but power and time) to read tens of terabytes of data to find what you are after, however if your cloud storage provider charges you for data volume read, the same activity could have a significant cost associated with it.

The notion of vendor-lockin is also relevant at this point, as your storage provider's supported retrieval/processing mechanisms may make switching providers difficult or cost-prohibitive **if** you want to change. An excellent treatment of this point as it applies to software can be found <a href="https://blogs.oracle.com/bmc/the-economics-of-software" target="_blank">here</a>, and much of the article can be applied to cloud services.

Given these aspects of cloud storage, it is not surprising that the choice of cloud storage is non-trivial.

## Taking another perspective

The simplest view of cloud storage products is where you state "I have data, I want to put it somewhere." There is nothing inherently wrong with this view, but it does skip a few important steps in the data lifecycle. I am going to propose a different way of starting the conversation: I have data, and I want to _do something with it_.

What might you want to do with your data?

- I want to store data durably in a second, off-site, location and only intend to access it in the event of a major loss (long <a href="https://en.wikipedia.org/wiki/Recovery_time_objective" target="_blank">RTO</a>).
- I want to store data durably in a second, off-site, location and intend to access it frequently.
- I want to store more data than I have capacity on-premise, an want to use an external provider to handle the extra that I don't access often.
- I want to be able to share portions of the data.
- I want to be able to perform computation or other actions on the data (using on-premise or other compute resources).
- I want detailed audit and access logs protecting my data.

This is a non-exhaustive list, of course, but covers many of the most common use cases or requirements for data. Typically, when people jump to "I want to put my data in the cloud", they are thinking about the first point, and only the first point. Let's dig into that one a bit.

## Cloud storage as Other-People's-Disks

When a cloud storage journey first begins, it is usually due to the need for off-site backup and the requirement that the disks simply be located somewhere else, with no specific requirements on geographic or political jurisdiction. Taking this requirement and evaluating various services' pricing models, there's a pretty significant range in the cost to store data with different providers.

For illustration, I will give approximate monthly costs to store 10TB of data in each of several popular providers, and where a provider has multiple options I will choose the least expensive options that provides 'instant' (a time-to-first-byte of seconds or minutes) access to any part of the data.

- Amazon S3 Infrequent Access: 125USD
- Amazon Cloud Drive: 50USD
- Azure Blob Storage LRS Cool: 100USD
- Microsoft OneDrive: 10USD
- Google Cloud Storage Nearline: 100USD
- Google Drive: 100USD
- Backblaze B2: 50USD
- Backblaze (Traditional): 5USD (per computer, unlimited backup)
- Crashplan Business: 10USD (per computer, unlimited backup)

Recall that the only requirement is that the data is stored durably in an off-site location, and for this service we can pay anywhere from 5USD per month to 125USD per month (there are more expensive providers, but I have not included them). Only a small part of this variance can be explained by differences in durability (multi-region vs multi-datacentre vs single-datacentre) or retrieval options (API vs installed/web application).

Remember when I said earlier that when you are choosing a storage provider, you're choosing an ecosystem? Now is a good time to talk about that as it will help explain the rest of the price variance.

> <a href="https://onedrive.live.com/about/en-US/plans/" target="_blank">Note</a> that for OneDrive, data beyond 5TB per user requires a request made to Microsoft.

## It's more than just the data

Let's take the least expensive option on the list, the Backblaze Computer Backup option for businesses, priced at 4.17USD per month (50USD per computer per year) for unlimited backed up data. This gets you an application (for Windows and Mac) for automating backups, shipped hard drive/thumb drive for larger restores (for additional cost), and a web application for restoring your data.

Backblaze <a href="https://www.backblaze.com/blog/vault-cloud-storage-architecture/" target="_blank">does not provide</a> multi-datacentre redundancy of a single piece of data. If their <a href="https://secure.backblaze.com/press/Sacramento_Data_Center.pdf" target="_blank">datacentre</a> were to go offline, your data would be unavailable. If their datacentre were to be lost, the data would be unrecoverable.

Backblaze does not offer any form of computation next to your data, so scanning backups to produce analytics, resize videos/images, or even searching for content is only possible by first recovering the data to a location with compute capacity.

Automated backup and restore via CLI is not an option using the computer-backup offering, but _is_ available when using their B2 product. Note, however, that the datacentre limitation above <a href="https://help.backblaze.com/hc/en-us/articles/218485257-B2-Resiliency-Durability-and-Availability" target="_blank">still applies</a> to the B2 product. The computer backup product does not provide automated ways of restoring single or selected files as part of automated workflows (such as bringing last year's posters for an art festival out of cold-storage to update them for this year).

Restores of smaller amounts of data (tens of megabytes) is quite responsive and files can be retrieved in minutes, however restores of several gigabytes can take an hour or longer to prepare before you can receive the first byte.

So what does B2 get you over the cheaper Backblaze offering? Specifically, B2 is targeted as a backend service, and is not intended to be end-user facing, as it provides object-level storage mechanisms, and CLI/API access similar to Amazon S3. Backing up a laptop is more complicated using B2 than the simpler computer backup offering, but restoring specific files via automated process is considerably easier and can be integrated with existing processing workflows. B2 provides fast (seconds) access to the first byte of any object you have stored in it, and does not require the same preparation time as the computer backup product.

## Paying more, getting more

When looking at the most expensive option in the list, Amazon S3 at 125USD per month, it is important to understand what that additional cost is purchasing, and whether or not the additional features provide value to your business. I won't dive deep into the others, but the Azure and Google Cloud storage options also provide many of these same, or similar, benefits for their increased cost.

- Extensive integration with the rest of the provider's (AWS, in this case) product catalog
- Fine-grained billing, reporting and audit tracing of access
- Mature encryption and key management services for controlling data privacy and integrity
- Multi-datacentre redundancy that can suffer the failure of at least one datacentre without impacting availability or durability
- Practically unlimited retrieval and upload throughput, with low latency and accelerated retrieval and upload options
- Integration with Import/Export services for bulk import/export of tens or hundreds of terabytes at a time
- Support for hybrid data presence with on-premise storage gateway appliances
- Integration with lower-cost archive solutions for rarely-accessed data
- Ease of moving your data to another provider

When you choose to store data on AWS, Azure, or Google, you are making the decision that you want to be able to leverage those ecosystems with your data, either now or in the future, and are paying for that opportunity. When making these types of decisions, it is important to evaluate whether there is enough value to your business in this extra cost.

## Get good advice; make informed decisions

When choosing a cloud storage provider, the choice is one that the future of your business, and any subsequent technology decisions, will need to work with. It is a decision that should factor in a great many things, and cost for storage is only one part of that decision.

If you or your business is interested in adopting a cloud storage provider for your needs and would like an expert to guide the decision making process, I encourage you to <a href="https://www.flyingfortressit.ca/#contact" target="_blank">drop me a line</a>.
