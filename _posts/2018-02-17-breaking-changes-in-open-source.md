# Introducing Breaking Changes in Open Source

In today's software world, your project depends upon 3rd party software that you did not author. Even if you examine the code of the packages you import in your project, you still don't know what your OS of choice and its dependencies do, or what your cloud provider does behind the scenes. This is because we don't have the time (or knowledge), or permissions to read the code (proprietary).

In this post we discuss how we can get latest updates without breaking our app.

We can _trust_ established projects that are maintained and have policies in place for security issues, contributions, releases and so on. After all you want to focus on your domain and deliver a great product.

## What can Open Source maintainers do?

If you are working on a project that is not ready to be used in production, it is a good idea to clearly indicate the development status of the project, so users don't complain later about breaking changes. Even if the project is under your personal Github handle and not under an organisation, you should still be clear about development status and releases.

* Use [SemVer](https://semver.org/) along with git tags
* Use [Github Releases](https://help.github.com/articles/creating-releases/) (of course this applies if you're using Github)

## How can you protect your app against breaking changes?

Before opting to use a 3rd party project, look in their README/documentation files to find out what their policy is about releases. As an example, [CoreOS](https://coreos.com/releases/) has 3 different channels for releases: `stable`, `beta`, and `alpha`. Chances are smaller projects do not have 3 different release channels, but they might follow [SemVer rules](https://semver.org/), or tag their releases via git tags.

### Package manager

A package manager is a very useful tool in software world and there are a few around for different programming languages, and to name a few: [Cargo](https://doc.rust-lang.org/cargo/) for Rust, [Composer](http://getcomposer.org/) for PHP, and [Godep](https://github.com/tools/godep) in Go. There are many more and listing all of them is out of scope for this post.

In a nutshell, a package manager allows you to use a specific version of a 3rd party library/package in your project and protects you from getting unexpected changes, even if the project doesn't follow SemVer rules. This can be done by specifying the git hash. The problem with a hardcoded hash instead of a semver rule, is that you're “stuck” to a specific version and you won't get further updates unless you change the hash in the corresponding file.

Whereas if the project was using SemVer, you could say that I want to get newer versions that are new features and bug/security fixes for version 2, but not breaking changes. You can automate this with a  CI job that runs every few days even if there are no new commits in your project and ships the new docker image (this process varies for each organisation).

### Fork

Depending on your use case, forking the project on Github, might be a good idea and you can maintain it yourself. You can still merge changes from upstream if you want to audit them first.

### Automated tests and CI Server
Hopefully, your app won't be shipped in production without you noticing about a breaking change. In order for you to notice, you need to have automated tests in place, that ensure your software does what it was supposed to.

If a breaking change is introduced, your tests will fail, so you will know something is wrong and start investigating the issue and eventually find the breaking change on 3rd party code.

Assuming that in our application we treat `master` branch as the one with the stable version, we can have our automated tests run on a CI server (like [TravisCI](https://travis-ci.org/)) before merging our changes to master, and depending on your organisation you might be able to run tests on CI on every commit.

### Run your build periodically even when there are no contributions

Assuming that you create a container image in your CI, you could have a trigger/hook that frequently runs the builds.

* In your build process, you get the latest version of your dependencies and if your tests fail you get notified.
* This approach allows you not to worry about vendoring your dependencies and continue getting bug fixes / new features.
* If a build fails because of a breaking change, you can decide how you want to handle it. You can update your project(s) or vendor the package with the breaking change, until you are ready to upgrade.

## Summary
Depending on your use case / organisation / preferences, one of the approaches might seem more appropriate to you than another. I'm happy to keep the conversation going and hear your ideas, feel free [reach out to me on Twitter](https://twitter.com/GeorgeGkirtsou)!
