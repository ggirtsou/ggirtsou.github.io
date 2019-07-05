---
layout: post
title:  "What makes a good engineer?"
description: "My take on what I think makes a good engineer based on my learnings"
date: "2019-05-07T23:36:00+00:00"
tags: "software engineer teamplayer productivity"
---

There are a few traits that I've identified over the years that in my opinion, make up a good software engineer:

## You learn and improve

Technology is moving at a very fast pace. Even if you're working with a specific stack, tech continually changes. Being able to learn new things quickly and adapt is critical.

## You are interested in learning the business domain

If you learn about the business domain, you understand the context, and you know why you're doing something, rather than do what others tell you. It can make work more interesting, and you stay around for longer (which is beneficial to the company as well as they save on hiring cost).

## You are pragmatic, professional and do not over-engineer or optimize prematurely.

Being pragmatic means, you understand when to do what, and spend time on the right thing. If a feature needs to be delivered quickly, you can't start writing a database from scratch (unless that's the product) so you combine the right existing tools and technologies to make it happen.

Being professional means sometimes saying no, and understanding what the commitments you're about to make — if for whatever reason a feature is delayed or blocked, informing your manager/stakeholders promptly is essential so they can make an informed decision.

Being kind and respectful to your colleagues helps to maintain a healthy relationship and avoid unnecessary tensions/conflicts.

Not over-engineering is to go with a simple design so that others can maintain it. Complex design does not prove that one is smart.

Technologists become excited with the idea of making things fast, and sometimes get carried away. Know when to spend time optimizing (and not overly optimizing) and find the balance. If you shift your focus on optimizing things, you do not spend time on what the company wants to deliver — fast iterations and standing out from the pack matters in a competitive market. You could also risk delaying the project because time was spent on over-optimizing a specific part.

## You deliver tested code with meaningful abstractions

Writing tests is great, but using TDD is even better! When you start with a test, you write the minimum amount of code required to make it pass, and iterate on that until that function is ready. TDD can help reduce complexity and protects you from writing tests that adhere to your current code, which could already have bugs. 

There are different types of tests, and a good developer must at least know the difference between unit and functional tests.

Some time ago, I was in favour of orchestrating microservices in a test environment and test their input/output and checking that messages went through OK. However, David Farley, author of [Continuous Delivery](https://www.continuous-delivery.co.uk/) book, told me in person if you have to do this kind of testing, you're better off writing a monolith to make your life easier.

Keep that in mind when next time you try to orchestrate them with `docker-compose` in CI. It's nice that you want to make sure your data pipeline works as you want it, but there's a more straightforward way: message contract frameworks like Protobuf ensure that your code breaks in CI if contracts change and your code hasn't.

## You develop software with security in mind

Multiple layers of security are required in today's world, and you should try to minimize the attack vector as much as possible. For example, an internal service should not be publicly reachable.

Following [OWASP 10 rules](https://www.veracode.com/directory/owasp-top-10) is a start and can take you a long way, but is not all you can do. Every layer needs to be locked down. Do not leave unnecessary ports exposed as it allows malicious users to gather information about your system and use known vulnerabilities against it. Successful attacks not only have financial implications for organizations but damage their reputation causing customer trust to decline.

## You mentor other colleagues

Improving yourself and learning is excellent, but passing that knowledge to your colleagues is even better! Pairing with them (and alternating who's driving), giving actionable feedback on how they can improve, and what areas they should touch on helps them level up. Having the right mentality and keeping an open mind can make a huge difference.

## You communicate ideas clearly and contribute to code reviews and architecture

Clear and coherent communication is vital in team discussions so you can effectively get your point across.

Participating in architecture sessions allows you to understand how the different services communicate and what different components are involved. You can then understand how what you're working on, fits in the grand scheme of things.

## You speak other people's language

No, I don't mean a foreign language, but you dial the technical terms and buzzwords down, so people who work in other roles (less technical) can understand you. Speak the user's language as well. Try to think you are the user and make it useful for them.

## You ask the right questions and go from a vague idea to a solution

Do not expect to get a fully scoped idea, or the exact specifications to develop a feature. Reach out to the right people in the company and ask the right questions to gain the necessary knowledge and deliver a working solution. Do research, find people who're going to use your software and understand their problems.

## You can effectively manage your own time

Time management is essential. Distractions are everywhere (@here), but work has deadlines. Be disciplined and focus on work instead of distractions to achieve your goals.

## You know when to stop and avoid burnout

I cannot stress how important this is - burnout is real. We all faced it. Being able to recognize it, respect your limits and ask for time off to "charge your batteries" is a must. Failure to do so results in loss of productivity and stress increase. People like to work hard, but nothing positive comes out of crashing.

You are less likely to experience burnout if you work in a team where work is exciting, challenging, rewarding, and you enjoy working with your teammates.

## You are not afraid to ask for help when you are stuck

Don't be the person who spends days blocked and stubbornly doesn't ask for help. There's no need to be embarrassed. Don't think others are not smart enough to help you. Working in a team is supposed to be collaborative, so speak to others about what you're working on, and bounce off ideas.

A good way to tackle this is to set the 15-minute rule: you work to fix the issue you're facing, take notes of the things you tried, and if you don't find a solution or have an alternative approach in mind, ask a colleague for help.

Getting stuck is not useful for someone's productivity and doesn't provide any value to the company.

## You can take feedback from your manager and peers

Constructive feedback is what makes us better, listening and acting on feedback is important for growth and to help the company meet its goals.
Keep an open mind, it is difficult to have others telling you what they think about you, but it can help you improve. Be grateful when people give you honest feedback as well. Don't hide behind your finger and think about how you can take that and turn it into actions.

## You allow others to speak their mind and don't interrupt them.

Self-explanatory :)
