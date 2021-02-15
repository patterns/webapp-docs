---
description: "\U0001F44B  We're so excited you're interested in helping with isgood.ai! We are happy to help you get started, even if you don't have any previous #techforgood or open-source experience :)"
---

# Contributing

## First Things First

1. New to \#techforgood projects? take a look at the [Solutions for Humanity website](https://forhumanity.org.au).
2. New to open source? take a look at [How to Contribute to an Open Source Project on GitHub](https://egghead.io/courses/how-to-contribute-to-an-open-source-project-on-github)
3. Familiarize yourself with the [isgood.ai Code of Conduct](code-of-conduct.md)
4. Learn [how the community operates](https://isgood.ai/toolbox/)

## Overview of our Codebase

The greater isgood.ai project has 3 layers:

1. WebApp Presentation Layer.
2. Backend, API and Data-Service Layer.
3. AI & Data-Platform Layer.

Layer 1 defaults to javascript, while layer 3 defaults to python.  Layer 2 is a combination of javascript, python and open-api standards.

{% hint style="info" %}
Tech stack on Stackshare -&gt; [https://stackshare.io/isgood-ai/beta](https://stackshare.io/isgood-ai/beta)
{% endhint %}

Collaborative decision making about tech stack decisions made on our [Loomio](https://www.loomio.org/sfh-isgood-ai-product/).

As general outline, our contributors spend most time with [Node](https://nodejs.org/), [React](https://reactjs.org/) & [Python](https://www.python.org/) coding languages, [PostgerSQL](https://www.postgresql.org/) and [Prisma](https://www.prisma.io/), along with [Material-UI](https://next.material-ui.com/).    
Our app base is [Blitz.js](https://blitzjs.com), so you MUST be familiar with this.   

note: _love the Blitz.js inclusive community and tech approach. If we find issues or can add back to this project and community, it would be very cool to do so_😍

## Open-Source Public-Good Principles

As a \#techforgood project, we have agreed to the [Digital Development Principles and Open-Source Licensing](https://www.loomio.org/d/C2gOcrqu/digital-development-principles-and-licensing), at all times when it is in the public interest and for the public good.  In effect, this means by default all of our code and scripts are [open-source by default](https://www.loomio.org/p/Kr1SHvs5/open-community-licence-where-applicable)![](../.gitbook/assets/osiapproved_1.png) , with a review of any private-repo scripts every 6 months to enable them to become open-source where public benefit outweighs risk.🎯 _isgood.ai risk work-group will be publish more info on isgood.ai website._

## Code Management Best Practices

### Coding Style & Commenting

We encourage you to follow the following general guidelines to help you team mates and leave behind code that can be worked with in the future by other developers.

* Do not write excessively long lines of complex code. Split them out into multiple lines. Today's compilers do not benefit much from dumping everything in one long line of code
* Remember that the people coming behind you also need to understand your code, they may not necessarily be at the same level as you so keep complexity to a case where it absolutely demonstrates tangible benefits.
* **Comment. Comment. Comment.** Explain why you did something and any other options you may have considered. Do this in an obvious comment block that stands out. It will likely help solve a future bug or a feature enhancement.
* We use an automatic code formatter called [Prettier](https://prettier.io/). Run `yarn prettier` after making any changes to the code. You can check the status of your code styling by simply running `yarn linc`.  If you are unsure about something, looking at [Airbnb’s Style Guide](https://github.com/airbnb/javascript) will guide you in the right direction.



