better-specs
============

[![GuardRails badge](https://badges.production.guardrails.io/dwmkerr/better-specs.svg)](https://www.guardrails.io)

(For the original post please go to [Better Specifications](http://www.dwmkerr.com/better-specifications/).
This repository contains examples of how pull requests and so on work with markdown specifications.

Specifications are absolutely key to the success of a project.

Unless you have a good definition of what your project is *supposed to be*, there's no way you can deliver it. A specification is the contract between you and the client, the basis for technical designs, quality assurance test plans, operational readiness, and much more.

I'm not going to talk about how different teams do specs, what works and what doesn't work. I'm going to make the statement that **the better that specifications are handled, understood and controlled, the better for everyone** - Project Managers, developers, testers, operational teams and customers.

If there's anyone who's on the fence about whether specifications are important or not, [Joel Spolsky's series on Painless Specifications](http://www.joelonsoftware.com/articles/fog0000000036.html) is a must read, he makes the point exceedingly well and I'd definitely recommend reading the articles.

I'm going to describe an approach to functional specifications that I think has a lot going for it. To developers it should look very familiar and (hopefully) appealing. To non-developers, the approach may not be so familiar, but the potential benefits should speak for themselves.

### Specs Right Now

OK - the introductions have been made. So how do we represent specs at the moment? Here are some common ways.

1. **Text files**. Specs are text? Well, sometimes. They might also be images, sometimes diagrams help too. But text can work.
2. **Word documents**. A little like the above, but with the facility to use tables and images and so on.
3. **Web Pages**. Perhaps more common nowadays, specs can be written on online systems like Sharepoint (just documents really, but with better multi-user support),  Google Docs or Bug Tracking/Wiki type systems.
4. **BDD Tools**. Whether using tools or not, BDD specs are files that state functionality in a more strongly defined format. 
5. **Tests**. Kind of similar to the above - depending on what you're writing or the tech expertise of team members, some teams opt for the bulk of their specs in the form of tests.

All of these systems have pros and cons. Some have many more cons, and some balance out better on different types of projects.

## A Better Way

So here's a suggestion of a better way.

> **Specs are markdown files in a repository. That's it.**

Now I'm going to show you why this is a good idea.

### Specs are text. Ish.

Pure plain text is a bit hard for specs - it can be helpful to have bullet points, headings and so on. But word processing tools are not always the best answer - you're tied to a specific tool, and unless you're working with people who all know how styles, track changes or the specifics of the tool work, you can spend more time messing around with formatting than you'd like.

Try comparing and rationalising two versions of a complex document that have gone out of sync, it's a nightmare.

Here's a snippet of a markdown spec:

```
Overview
--------

This spec is for the login screen of the application. The overall design of
the screen is in the file 'mockup.png'.

The Controls
------------

* The 'username' box accepts alphanumeric characters.
* The limit of the 'username' box is 120 characters.
* The tooltip for the username box is 'Enter Username'.
* The password box accepts any characters and is limited to 120 characters.
* The tooltip for the password box is 'Enter password'.
```

It's readable in it's raw form. This is how it looks on GitHub:

{<1>}![Login Screen Spec](/content/images/2014/May/LoginScreenSpec.png)

See the real thing at [github.com/dwmkerr/better-specs/blob/master/login/login.md](https://github.com/dwmkerr/better-specs/blob/master/login/login.md).

(These specs are just made up ones for this article).

The formatting is readable even in plain text mode, but many modern day tools understand how to show markdown in a slightly nicer way (I'm writing this post in markdown - [Ghost](https://ghost.org/) uses markdown for blog posts). You can print it and understand it, email it to recipients in plain text mode, and importantly there's no fiddling with formatting.

If you haven't used markdown before, give it a try on [StackEdit](https://stackedit.io/), it's an online markdown editor - you can have a play with it.

### Specs are Version Controlled

Specs need to be version controlled. You need to be able to see a history of a spec, who changed it, when they changed it and what the change was.

Even more useful - you should be able to diff specs - what changed between two versions? This is hard to do with programs like word, with version control systems like git, it's a piece of cake. Take a look:

{<2>}![](/content/images/2014/May/LoginScreenDiff.png)

We can see easily who changed this spec and when, we can compare revisions.

This not just a powerful feature - it's a required one. Developers and testers can see what has been added, removed or modified. So can project managers.

This is a diff that developers will understand - the red and green make it clear for non-devs too. Modern systems like GitHub can take it further:

{<3>}![](/content/images/2014/May/LoginNiceDiff.png)

Pretty clear what's going on.

### Pull Requests

Let's take the version control aspect further. A spec should have one owner, one person who can press the button and say 'yes, this is in'. There needs to be one owner, because a change to a spec is like a change to a contract - it could represent hours of developer time, cost increases, release date issues and more. There's impact, there are consequences.

So using services like GitHub or Bitbucket can help here. Anyone can make changes to a spec, but a single approver has to review those changes and decide whether to bring them in.

{<4>}![](/content/images/2014/May/LockoutLogic.png)

[See this pull request on GitHub](https://github.com/dwmkerr/better-specs/pull/1/files?short_path=d645d03#diff-d645d03c7459b43c1e030eeb13d1245b)

Pull requests support comments, discussions, diffs and all sorts of useful things. No one can get something into the spec until the approver has OK'd it. 

It also gives the approver a single point where they can action the changes, perhaps raising a task for a developer to work on the changes.

That pull request can also be *linked to* later - in the bug tracking or feature management system, an issue to implement the changes in the pull request can be made - and the implementer always has a link to the *exact* change.

> Don't put the change to a spec in a work item. A work item *refers* to a change in the spec.

This is very useful. In the pull request shown (which you can [see here](https://github.com/dwmkerr/better-specs/pull/1/files?short_path=d645d03#diff-d645d03c7459b43c1e030eeb13d1245b)) has one innocuous extra line (which we see in green) stating that the user is locked out after three failed password attempts. This isn't in the spec, not until we accept the pull request. And in this case instead we can comment to the person who raised it:

{<5>}![](/content/images/2014/May/LoginPullReqComments.png)

I had to make a contrived example and fake a discussion between myself and myself, but I think seeing how this looks helps make the point.

### What About Rich Media?

Keep your rich media. Keep images, tables and diagrams - just check them in alongside the spec and link to them from the spec. You still get version control, pull requests and a history. Depending on the media you might even get a nice diff representation - check out this commit:

{<6>}![](/content/images/2014/May/LoginImageDiff.png)

[See the actual commit here](https://github.com/dwmkerr/better-specs/commit/8a1224812db2ae4909dfb5a30f8483b1ca96ed18?diff-0=0-100)

You can see the image before, after or even use the slider to see what has changed. The rich media is *supporting* media - it's still the spec that's boss.

Don't throw away your powerpoint presentations, visio files or anything else, but make the spec king and these files support it. Got a big table of information? Do it in excel or google sheets, that's the right tool for the job - but version control it with the spec.

### Persuading Others

The hard thing about this approach might be persuading those who are not used to it to use it. 

To developers, I imagine this approach has immediate appeal. We know that an email chain of timestamped word documents or powerpoint presentations is a nightmare to maintain as it evolves, and that versin control systems are critical to managing shared work.

To business people who are not used to version control or markdown, it might seem like a nerdy, inefficient way of doing things. But the points above are quite compelling. If you have strong arguments for or against, comment and I'll update the article.

### Useful Resources

It's worth pulling together some useful further reading.

* [Joel Spolsky's series on Painless Specifications](http://www.joelonsoftware.com/articles/fog0000000036.html) - A well written series on why specs are so important.
* [Markdown](http://daringfireball.net/projects/markdown/) - The official homepage
* [StackEdit](https://stackedit.io/) - Have a play writing markdown and see it rendered.

## Final Thoughts

I've never used this approach in a team - I am writing specs for a side project like this at the moment, but this is a one-man project (for now).

Have you tried this approach? Any success stories or experiences of it failing? I'd love to know, so comment if you've got some experience on this one.

P.S. - This page was written with markdown!
