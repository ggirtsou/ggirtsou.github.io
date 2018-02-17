---
layout: post
title:  "Microservices Go-live checklist"
description: "What criteria do your microservices need to meet to be deployed?"
date: "2018-02-17T21:07:39+00:00"
tags: "microservices go-live"
---

More and more organisations break up monoliths (formerly known as "app") in smaller services
and adopt microservices architecture pattern and they communicate in an asynchronous way via Event Sourcing. The main benefits are:

* ability to scale different services as needed,
* allows you to use the right programming languages for the domain, design architecture specific to that service,
* risk is minimised when a service fails as the entire platform/product doesn't go down,
* service oriented teams have better knowledge of a specific domain and clear view of how different services come together.

# Go Live Checklist

## Revise architecture, get rid of Single Points of Failure

Make sure everyone is happy with the current architecture, and if you need to deliver fast,
plan when those fixes will be made, make sure everyone is on the same page, and document those decisions.

Additionally, you want your service to be highly available:

* deploy in multiple availability zones and regions,
* replicate data multiple times

And secure ([security](https://www.owasp.org/index.php/Top_10_2013-Top_10) is a huge topic and below list is by no means exhaustive):

* hide in a private network the resources that don't need to be publicly accessible,
* protect the resources that are exposed to public internet.

## Documentation

Ensure your documentation (README/Wiki entries), provide enough information about your app:

* what it does, provide enough context about the problems it solves,
* how to install it,
* how tests are run,
* Usage (`--help` output for binaries with available flags).

Your microservice should be fairly simple and do very specific tasks. If you find it does
too many things, consider breaking it down to more microservices.

## Containerize your app

There are many benefits in containerizing your application, described [here](https://cloud.google.com/containers/).

In a nutshell, your artifact is a [Docker image](https://www.docker.com/) that is deployed and managed by a container orchestration framework, such as [Kubernetes](https://kubernetes.io).

## Healthcheck and readiness endpoints

To be used by the container orchestration framework to determine if the app is healthy and
ready to accept connections.

Possible healthcheck values:

* healthy (app and its dependencies are healthy)
* degraded (a dependency has degraded status)
* unhealthy (app or a dependency is unhealthy)

Degraded performance means some operations will fail.

## Metrics endpoint

You can create meaningful dashboards (for example in [Grafana](https://grafana.com/)) by
leveraging the power of metrics. This is useful to see how your app is behaving, for example
memory consumption, GC pauses, error rate, HTTP status codes, and whatever else is useful
when troubleshooting your application.

A popular tool for metrics collection is [Prometheus](https://prometheus.io/).

## Logging

Structured logging provides useful insights on what your app does and can be aggregated and parsed in a
service like [Splunk](https://www.splunk.com/) or [SumoLogic](https://www.sumologic.com/).

## Set up alerts

Create alerts based on business and operations logic, here are some examples:

* no files received from 3rd party provider within 6hrs,
* disk usage is above 75%,
* error rate is above a certain threshold rate for 15mins,
* service is unhealthy,

_Note:_ Finding the right value for a threshold sometimes takes time, and should be
adjusted as you don't want to be alerted too often as you'll end up ignoring, or even worse
missing alerts due to excessive noise.

Think about what threshold is acceptable for your service and investigate why an alert was
triggered, and if necessary adjust the threshold.

## Backups and restore plan

Have a backup strategy as well as a way to restore from previous backups. It is very
important that your teammates are familiar with these processes and you have tested they
work.

You don't want restoring from a backup to fail in a critical situation.

You also want an alert if backups are not being taken, this can be achieved by your backup
service exposing relevant metrics and you setting up alerts for all apps that have their
data backed up.

# Resources

For more on distributed systems, reliable microservices, and event sourcing I recommend the following resources:

* [Distributed Systems by Maarten van Steen,‎ Andrew S. Tanenbaum](https://www.amazon.co.uk/Distributed-Systems-Maarten-van-Steen/dp/1543057381) also freely available [here](https://www.distributed-systems.net/index.php/books/distributed-systems-3rd-edition-2017/ds3-sneak-preview/),
* [Production-Ready Microservices](http://shop.oreilly.com/product/0636920053675.do) by Susan J. Fowler,
* [eBook download for Event Sourcing and CQRS by Microsoft](https://www.microsoft.com/en-gb/download/details.aspx?id=34774)
