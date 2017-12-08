---
title: "AWS Certifications"
subtitle: "Drinking the orange Kool-Aid"
date: 2017-12-08T09:00:00-06:00
author: Mike Himbeault
description: "Experiences preparing for and writing three AWS certifications, and comparing the resulting benefits to my experiences with academia during my two degrees."
categories:
  - AWS
  - Certification
# tags:
#   - 
---

After two years immersed as a software developer and infrastructure architect focusing on AWS solutions and public cloud architecture in general, I felt it was time to sit down and write a few AWS certification exams. These are my thoughts on the certifications, exams, preparation, and value of tem after the fact.

<!--more-->

## Getting into the mood to write more exams

My education history includes an undergraduate honours degree in mathematics, as well as a Masters degree in computer engineering focusing on computer network security. You can find a link to my thesis on our [credentials](https://www.flyingfortressit.ca/#credentials) page. After finishing my M. Sc. I was rather tired of academia, and it took me several years before I considered writing a professional certification, such as the AWS certs.

I started considering writing my AWS exams, shooting for the Solutions Architect - Professional exam, in December of 2016 after attending re:Invent. At that point I felt that I had a good handle on developing solutions on AWS but wanted to make sure that I knew what I thought I knew, as a matter of professional diligence. Writing the exam was something I viewed as both a way of accomplishing that, as well as giving any others that I work with some assurance of that as well.

## Beginning preparations

Fast forward a little bit to February 2017 when I signed up for Linux Academy as a way to begin preparing to write the exams. A couple days into the free trial I found that I was really enjoying the content, and jumped onto an annual subscription. So far I have watched hundreds of videos on a variety of technical topics, and have found the content generally high quality, and the videos are well suited to me listening to the audio on the drive to and from work every day.

Over the course of several months, I completed the courses for the Developer Associate, Solutions Architect Associate, Solutions Architect Professional, as well as a variety of accessory AWS video courses. These videos gave me ideas for small projects I would tackle with new services or products in order to familiarize myself with them in more detail.

There is no replacement for hands on experience with a service, that's for sure.

In August 2017, on the recommendation of a colleague, I picked up the practice exam sets for all five AWS exams from WhizLabs. These were an excellent, and inexpensive, supplement to the Linux Academy training content, and helped significantly in preparing me for the exams themselves. It was around this time that my talk proposal was accepted for BSides Winnipeg 2017, which gave me a hard deadline to write my exams by.

I now had a goal: write at least two, preferably three, AWS exams before November 4 2017. Having finished the Linux Academy content and completed several AWS-focused projects of varying scopes and complexities, I was confident in my ability to talk to the topic however the certifications would be great ways to get exposure at the conference.

## Writing the exams

Originally, the plan was to write the Solutions Architect Associate and Professional exams a couple months apart to specialize and limit the scope of the preparation I needed to do. What ended up happening, however, was that I wrote all three Associate level exams one after another over a three week period. I still intend to write the Solutions Architect Professional exam, but that will likely be deferred to early 2018.

Registering for the exams was a moderately straightforward process involving a bit of first-time setup, and a bit more process than I was expecting, but none of which was onerous. In my city there is exactly one exam slot per week at noon on Tuesdays at a learning centre in the south end of the city. It's a reasonably convenient slot and location, and should be simple enough to get to. Note that since the Associate exams are over an hour, and the professional exams are a few hours long, planning to get there, write them, and get back on a lunch hour is not necessarily a reasonable expectation.

These exams are proctored exams, and you are given a controlled workstation (in my case a small netbook) in a controlled environment without access to external materials, and a piece of paper and a pencil. This was very familiar, and reminded me of university exams where limited materials were permitted, and most materials were provided.

I chose to write the Solutions Architect Associate exam first, as it was the area I felt most confident in. I arrived a fair bit early, not knowing what to expect, and found that I was the only person there during that time slot. The proctor showed me to the room, and we worked together to get the test environment set up, as this was the first time she had proctored an AWS exam (I will touch more on this later). Once set up, she left the room, and away I went.

Twenty two minutes later I was finished, and hit the final "Submit" button. The pass/fail result is given to you immediately in the time it takes you to spin in your chair a couple times, so you get that gut relief (if you pass) immediately. I returned the pencil and paper to the proctor, she finished the final steps (confirming that I had indeed returned all provided materials), and the summary email had arrived in my email inbox by the time I had reached my car in the parking lot.

The email contains your overall score, as well as a breakdown of your performance by category.

```
Overall Score: 95%

Topic Level Scoring:
  1.0  Data Security: 100%
  2.0  Implementation/Deployment: 60%
  3.0  Troubleshooting: 100%
  4.0  Designing highly available, cost-efficient, fault-tolerant, scalable systems: 100%
```

Based on the notes I took (and managed to remember after handing back the provided note paper), the test and I disagreed mainly on when Elastic Beanstalk and CloudFormation should be used.

I wrote the Developer Associate exam the following week, and finished in 12 minutes with 98% overall. The final exam I wrote was the SysOps Administrator Associate, which I knew going in was _by far_ my weakest knowledge base for a few reasons I'll cover later. The SysOps exam took me half an hour, and I scored 89% overall.

Overall, writing the exams was a positive experience, and I actually look forward to writing my last one or two in early 2018.

## Exam preparation retrospective

Looking back on the preparation materials, here's a few brief pieces of advice I would give past-me:

- There really is no replacement for hands-on experience when it comes to the real world, but when it comes to writing the exams, knowing the little pieces of information they choose to focus on is worth more. Note that this implies that the certifications do not cover enough to guarantee a person is going to know what they're doing without significant real world experience.
- The Linux Academy content was excellent, and covered the core concepts and information appropriately. Their practice exams (note that this is before the integration with CloudAssessments) were fine, but not as comprehensive as WhizLabs.
- The WhizLabs practice exams for the Developer and Solution Architect exams were _spot on_ and immensely valuable. I would say that about 60% of the questions on the exams themselves were represented almost exactly in the WhizLabs practice exams. This is, in no way, an endorsement of memorization, but if you've got a good understanding of the content and material, and have recently run though a couple practice exams, it will significantly speed up your completion time. That said, the exam questions were good, did not attempt to trick you, and if you knew the material like you should, the correct answer was always easily identifiable.
- The WhizLabs practice exam for the SysOps Administrator, however, was of far lower quality. The questions routinely included broken English, and at times were missing important nouns (or even proper nouns!). The exam itself for the SysOps exam was also much older, and tested on technologies that are no longer available in AWS (unless your account is already using them, like EC2 Classic or previous generation instances). This makes it difficult to get hands-on experience with some of the content of the SysOps exam, and forces book-style learning from the AWS documentation.
  - Note that the SysOps certification is only recommended for those with at least one other AWS certification, and I definitely agree with this recommendation. It tests small intricacies and details of services that will be well out of the field of view of someone just getting into AWS work.

## Certification value

To be clear up front: these certifications were worth every penny, and I will definitely be writing more.

As of November 2017, according to LinkedIn there are only five people in my city (Winnipeg, Canada; population about 700,000) with AWS certifications. All of those have the AWS Solutions Architect Associate (one of which I believe has lapsed), and one of them is myself. That is, the AWS certifications are still quite rare, and finding individuals both with the certifications, and with significant experience and in-depth knowledge of the services is very uncommon (which makes it highly valuable). In my city, having these certifications is a great way to get my foot in the door, both of potential employers and for consulting engagements or other opportunities. Being AWS certified is definitely a differentiator and will help you stand out against other individuals or companies that claim to "do cloud."

In the end though, these certifications are only 80-minute long exams and cannot possibly cover all of the knowledge and skills you might expect someone with these certifications to possess. In my experience, those that hold even the Solutions Architect Professional designation still have significant gaps in their knowledge and expertise that only only experience can fill. My extensive real-world experience spanning several years with AWS, combined with these certifications, uniquely prepares me to tackle any challenge, and to work with any AWS based solution. Unfortunately, I cannot say the same of all that hold the certifications, so buyer beware, as it were.

## Summary of thoughts

In short, the certifications were great for me, provided significant differentiating value, and gave me confidence that I do indeed know what I know.

That said, the certifications are not a degree, and simply cannot guarantee that a certified individual is truly competent and capable. When evaluating either a job applicant or consulting company (like Flying Fortress IT) that holds these certifications, it is always a good idea to ask for more information about other projects they have worked on to get a sense of how broad and deep their skills really are.
