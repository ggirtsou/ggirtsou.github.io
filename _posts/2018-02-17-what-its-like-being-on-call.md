---
layout: post
title:  "What is it like being on-call?"
description: "What are the challenges of being on call and why is it necessary?"
date: "2018-02-17T17:40:19+00:00"
tags: "on-call"
---

Being on-call means, you are responsible to fix an error, in a timely manner, when it occurs in production (time varies for each organisation).

On-call can seem scary, especially if you've never done it before, or if you are new to the services. If you are new to a company/team and you
are not familiar with their services and haven't had much exposure to their codebase, how can you fix issues?


## When am I ready to go on call?

Getting a good understanding of your domain is beneficial, because some alerts require some level of comfort with the processes, in order to
be resolved. If you're fairly new to the team/company these kind of alerts shouldn't be a blocker for you as someone is shadowing you.

What this means, is, after your investigation if you're unable to resolve an alert you ask your colleague about this alert and they can advise
you how to proceed.

That's a great thing, as you're not alone and you can benefit from their past experience! Of course that doesn't mean you should ping them
before doing your investigation as they don't expect to be pinged very often.

You might notice that at the beginning on-call takes up a lot of your time, even during work hours, but after a while you will be able to
better understand what you have to do to resolve an issue fairly quickly.

## How often are you on call?

It varies for each organisation. It is usual in Service Oriented Teams to be on call for a week, rotating with other members of your team.

In non service oriented teams, you choose on the calendar how long you want to be on call. However, I don't think it is healthy to be on call
for more than a week as it can have an impact on your personal life and you will get tired and not be able to perform well at work.

## Is on call useful just for the company?

In my opinion, it is beneficial to engineers as they get a better understanding of the services by resolving issues, even if they haven't
contributed to a particular repository.

## Are you responsible for all alerts?

### Service Oriented Teams

In Service Oriented Teams, you are responsible for services running in your domain. That's a good thing because you are not responsible for
something you can't resolve and you won't get an alert from another domain within the same business.

In Service Oriented Teams you focus on a specific business domain and you have more control over:

* designing and architecting,
* writing code and shipping to production,
* maintaining it during on-call and off-call,
* resolving non-software issues (such as hiccups in clusters within your domain)

### Non Service Oriented Teams

In non service oriented teams, there are multiple levels of on-call starting from System Engineering, and if is a bug with a service, it is
escalated to developers. The problem with this approach is that in level 1, even if it's a software bug, you will wake up at 3am from an alert, do the initial analysis and escalate it. This gets frustrating very fast, and clearly has an impact on your life. 

In organisations like this, cross team communication is not that great. It is usual members with extensive knowledge of the systems participate
in on call, and they get compensated extra depending on the duration they were on call.

## What happens if you want to go out, or are in a tunnel with no reception?

Being on-call doesn't mean you don't have life during that period of time.

As described above, when you are on call you're not alone. There's a colleague shadowing you, and if you don't acknowledge an alert in the
specified time set by organisation, then the other engineer gets alerted. This is a good practice because we're humans but it doesn't mean we
should get drunk during on call expecting the other engineer to take on our shift.

## A note on downtime

Let's say there's an imaginary company named `ABC Acme Example Soft` and our boss, Bob, told us the company relies on services being up all the
time. Any downtime results in customers considering going to competitors, and millions of revenue is lost.

Providing a robust product is linked to company's reputation nowadays. 

From a software and architecture point of view, company's engineers, must make sure there are no single point of failures, and if there are
they have to go to the drawing board to resolve those issues and design their services to account for failures, ensure they are scalable, data
are replicated and instances run across different availability zones and regions (latency!).

The on-call engineer can do so much, but it's not up to them to make everything from scratch shall a failure occurs.

![On call](https://pbs.twimg.com/media/CyYglEWXcAIcuf0.jpg:large)
_Pictured above: "Welcome to the cloud, here's the system, you'll be on call today" [source](https://twitter.com/mononcqc/status/803365410347352064)_

## How do you get alerted?

Usually, you install an application on your phone such as [OpsGenie](https://www.opsgenie.com/) or [PagerDuty](https://www.pagerduty.com/) and
you receive alerts there. If you're using [Slack](https://slack.com/) and there is a channel with all the alerts, you can get notifications from there as well.

Additionally, you can configure the alerting service to call you on your phone or
send you an SMS message (in cases where mobile data reception is bad).

## Your experience

I'd love to hear your thoughts and about your experience during on-call. Feel free to [reach out to me on Twitter](https://twitter.com/GeorgeGkirtsou)!
