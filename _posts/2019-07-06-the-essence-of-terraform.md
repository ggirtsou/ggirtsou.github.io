---
layout: post
title:  "The essence of Terraform"
description: "A thought experiment about cloud-agnostic led me to think about what Terraform really does"
date: "2019-07-06T16:21+00:00"
tags: "cloud agnostic terraform hcl abstractions"
reading_time: "3 mins"
comments: true
---

![The essence of Terraform](/assets/images/posts/the-essence-of-terraform.jpg "The essence of Terraform")

Photo by [Samantha Gades](https://unsplash.com/@srosinger3997?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/search/photos/perfect?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

Have you heard of [Terraform](https://www.terraform.io/)? It is a tool that allows you to provision your infrastructure. You describe your infrastructure in a configuration language called [HCL](https://www.terraform.io/docs/configuration/syntax.html), and Terraform takes care of the rest.

## How does it work?

Terraform tracks the current state of your infrastructure in [state files](https://www.terraform.io/docs/state/index.html), and performs a delta diff similar to how git does it and applies only the changes.

An example Terraform diff:

![An example Terraform diff](/assets/images/posts/terraform-plan.png "An example Terraform diff")

## Why?

I've heard people say their organization is cloud agnostic which  means they are not locked into a specific vendor and can switch with relatively low effort. Reason for changing vendor can be more competitive pricing somewhere else.

It sounded too good to be true and not pragmatic at all. Migrating hundreds of GBs of data requires planning and can take a significant amount of time. How often would you do that? Is it worth the effort?

So I put on my "curious George hat" as I wanted to explore further and understand:

* if it's possible for an organization to be cloud agnostic
* what are the tradeoffs

I brought it up at work to see what others think, and I did some research online. The short answer is that you can be in multiple clouds, but you cannot be cloud agnostic because if you do, the abstractions you have to create take away all the benefits you get from cloud vendors.

Such a concept would push you to think in terms of "VMs" and "disk volumes", as not all cloud vendors have the same products and options.

[Kubernetes](https://kubernetes.io/) is an option that can run in different cloud platforms, but at some point, you will use a cloud SDK in your apps. You build products around a vendor.

If you're interested in a lengthier explanation, [read this](https://www.finextra.com/blogposting/16840/cloud-native-vs-cloud-agnostic-what-conundrum-behind-the-hype).

So as part of that thought experiment, I started thinking about what Terraform does.

## The essence

If we simplify Terraform and exclude its state management and storage characteristics, we end up with a translation mechanism! That "translation" mechanism is simply reading HCL files and makes the appropriate API calls by using [providers](https://www.terraform.io/docs/configuration/providers.html).

In the simplest terms, you can say [AWS CloudFormation](https://aws.amazon.com/cloudformation/) does the same but takes JSON and YAML as input.

## Your experience

I'd love to hear your thoughts or whether being cloud agnostic is possible or not. If you know any projects that do that please [reach out to me on LinkedIn](https://www.linkedin.com/in/george-g-279883115/)!
