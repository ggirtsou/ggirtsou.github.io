---
layout: post
title:  "Moving fast gives you a competitive edge"
description: "The story of how I learnt that moving fast is essential in corporate world."
date: "2019-07-06T11:26:00+00:00"
tags: "startup iterations agile innovation"
reading_time: "3 mins"
---

![Moving fast gives you a competitive edge](/assets/images/posts/moving-fast-gives-you-a-competitive-edge.jpg "Moving fast gives you a competitive edge")

Photo by [Ian Schneider](https://unsplash.com/@goian?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/search/photos/perfect?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

This post is the story of how I learnt that moving is essential to get a competitive edge on the market.

## Demographics

My first job was at an Affiliate Network startup in Athens, Greece. The market in Greece is small, about 11 million people and only [3.5 million of them](https://www.export.gov/article?id=Greece-eCommerce-Overview) buy goods online.

![Greece's population is about 11 million people](/assets/images/posts/greek-population.png "Greece's population is about 11 million people")

## The Competition

With three networks operating in a small market, it is difficult to get merchants on board. Competing with companies that have deep pockets can seem daunting at first. So we set out to build a great platform that merchants and affiliates alike couldn't resist.

## Our Approach

Working closely with the CEO of the company, we came up with innovative ideas on how to make it easier for affiliates to promote content on different mediums.

Leveraging open-source technologies, and managed services we were able to iterate quickly, and within a few months, we had functionality running in production that was unheard of in Greece. AWS allowed us to optimize costs and not worry about scaling servers as you would in a datacenter environment. Our tools effortlessly served millions of page views daily.

## Some of the Challenges

Not only it was a fast-paced environment, but some of the problems were hard. We kept an eye on the cost. One of the tools was serving product inventory based on specified criteria in different formats such as XML, CSV, and JSON, and we allowed custom tag names. Making it easier for affiliates to use our tools was vital.

That meant I had to find a way to modify XML feeds on the fly dynamically in PHP. PHP does not do well with XML as it tries to load the whole file in memory and then start modifying it. With large XML files that weren't an option. I suggested we needed a Search Engine mechanism to index product inventory and generate the feeds based on the parameters each affiliate specified.

Sounded like a good idea, but that didn't cut it for us! We could do better! And we did. 80% of the generated feeds were created using default options (we had sensible defaults), so we had a cached version ready and swapped the {affID} placeholder using [sed](https://linux.die.net/man/1/sed), with the user's ID. Subsequent requests for the same feed served the cached version until TTL was expired.

We made it easy for them to create product grids and collages, custom feeds, SMS notification system for new leads and so much more.

At the same time, we migrated all data from the legacy platform DirectTrack to HasOffers and seamlessly integrated the tools inside the platform so that they could manage everything under one place.

## What happened in the end?

As I said, the competition was fierce. Other companies had access to lots of funding, but we didn't. I was let go and moved on to other adventures. It was a great learning journey for me, and I am grateful for that opportunity. That company is no longer trading.

## Your experience

I'd love to hear your thoughts and similar experiences. Feel free to [reach out to me on LinkedIn](https://www.linkedin.com/in/george-g-279883115/)!
