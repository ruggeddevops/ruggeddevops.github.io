---
layout: post
title: "Keeping Watch with Gauntlt for Rugged in Practice"
date: 2013-11-19 10:27
comments: true
categories: 
---
In a recent conversation with [@brandonprry](http://twitter.com/brandonprry) we asked him how they are using [gauntlt](http://gauntlt.org) at his company.

[@gauntlt](http://twitter.com/gauntlt): What does your company do and what is your role there?

[@brandonprry](http://twitter.com/brandonprry): We are game development shop and I am an Application Security Engineer which means I do security penetration testing of our applications and backend services.  Our games talk to a lot of backend web services and web applications.

[@gauntlt](http://twitter.com/gauntlt): How do you use gauntlt?
<!-- more -->

[@brandonprry](http://twitter.com/brandonprry): We are just getting started with gauntlt, but there are a couple of ways we started using it.

First, I added the arachni tests to check for XSS (cross site scripting) and injection attacks.  I added some login logic to our gauntlt attacks to engage with the application past the login page.  

Second, we have started using the [Garmr](https://github.com/mozilla/Garmr) attack to check for basic requirements on the page.  [Garmr](https://github.com/mozilla/Garmr) is a tool by Mozilla and checks a URL to meet Mozilla's security policy.  You have to sort through the output a bit, but it offers some nice features.  One of the gauntlt attacks we wrote checks to make sure that there are no new login forms.  If Garmr reports one of the login forms as 'skipped' of 'failure' we consider that a failure.  We use this as a way to see if any new login forms have been added to an application.  As a Application Security Engineer, I want to be alerted if there is a new login page somewhere in our application or stack.

[@gauntlt](http://twitter.com/gauntlt): Wow, that is pretty creative to use Garmr to look for new login forms.  Great idea.  We should make that a usage pattern in Gauntlt in the future.

[@brandonprry](http://twitter.com/brandonprry): Thanks.

[@gauntlt](http://twitter.com/gauntlt): Where does gauntlt fit in your deployment pipeline?

[@brandonprry](http://twitter.com/brandonprry): Currently this sits at the end, however we are already working on moving this upstream.   Right now I am the gauntlt master so it hasn't spread within the organization yet, but that is the goal.

[@gauntlt](http://twitter.com/gauntlt): Some people have called gauntlt script-kiddie prevention, what do you think of that?

[@brandonprry](http://twitter.com/brandonprry): Well, it makes sense.  Gauntlt can hook some of the popular scanners and make sure that at least a generic scanner won't detect anything glaring.

That said, Gauntlt wont find all the vulnerabilities I will find doing manual penetration testing, but I don't think that is the goal.  What I like about gauntlt is that I can find problems, write gauntlt attacks to replicate the issue and use that to reproduce the issue with the dev team.  I also like that it serves as a way to prevent security regressions.

[@gauntlt](http://twitter.com/gauntlt): Thanks for taking time to chat with us on this.

[@brandonprry](http://twitter.com/brandonprry): Thanks.
