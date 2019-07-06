---
layout: post
title:  "Introducing Breaking Changes in Open Source"
description: "Your app depends on 3rd party open source software - how do you avoid breaking changes?"
date: "2018-02-17T13:10:39+00:00"
tags: "open-source semver breaking-changes"
---

In today's software world, your project depends upon 3rd party software that you did not write. Even if you examine the source code of the packages you import in your project; you still don't know what the Operating System and its dependencies do, or what a cloud provider does as its proprietary code. It could be that we don't have the time (or knowledge), or permission to read the source code.

Let's explore the options on how to get the latest updates without breaking your software, and what you can do if it happens.

## Trust established open source projects
Established projects have a release process and are less likely to introduce a breaking change in a non-breaking version.

## What can Open Source maintainers do?
If you are working on a project that you would like to be used by others, clearly indicate the status of the project, and establish a release process.

* Use [SemVer](https://semver.org/) along with git tags
* Use [Github Releases](https://help.github.com/articles/creating-releases/) (this applies if you're using Github)

## How can you protect your software against breaking changes?
Before opting to use a 3rd party project, look in their README and documentation files to find out what the release policy is. As an example, [CoreOS](https://coreos.com/releases/) has three different channels: `stable`, `beta`, and `alpha`. Smaller projects do not have three distinct channels, but they might follow SemVer rules, or tag their releases by using git tags.

### Package manager
A [package manager](https://en.wikipedia.org/wiki/Package_manager) is a handy tool in the software world that allows you to use a specific version of a 3rd party library in your project, and protects you from getting unexpected changes, even when the library doesn't follow SemVer rules. To name a few: [Cargo](https://doc.rust-lang.org/cargo/) for Rust, [Composer](http://getcomposer.org/) for PHP, and `go mod` [subcommand in Go](https://blog.golang.org/using-go-modules).

#### How do they work?
Every package manager has a particular file where dependency versions are referenced. You can specify a git hash or semver version. When the package manager runs, it downloads the dependencies in a `vendor` (or similar) directory.

### Pros and Cons

**Git hash**
The downside of using a hardcoded git hash is that you're "stuck" to a specific version, and you won't get further updates unless you change it.

**SemVer**
If the project references a SemVer version, you can get newer versions with new features and bug/security fixes, but not breaking changes. You can automate this with a CI job that runs every few days and deploys the created deployment artifact.

### Fork
Depending on your use case, it might be a good idea to fork the project and maintain it yourself. You can still merge changes from upstream if you want to audit them first.

### Automated tests and CI Server
A CI pipeline with automated tests (that at the very least check the critical parts of your application) can identify breaking changes. Build code even if your code hasn't changed, as upstream dependencies continue to evolve.

If a breaking change is detected, your tests should fail because the 3rd party library API has changed, and you know something is wrong, so you investigate the issue and eventually find the breaking change.

## How to fix a broken upstream dependency?
You can update your project to use the updated API, or if you are in a hurry, vendor the library with the breaking change until you are ready to upgrade.

Depending on your use case/organization/preferences, one approach might seem more appropriate than another.

## Examples of breaking changes in real life

* [logrus, a popular logging library in Go](https://github.com/sirupsen/logrus/issues/451)

## Your experience

I'd love to hear your thoughts and about your experience during on-call. Feel free to [reach out to me on LinkedIn](https://www.linkedin.com/in/george-g-279883115/)!
