---
layout: post
title: "Migrating from Angular to React"
date: 2017-11-12
permalink: /migrating-from-angular-to-react
---

At Color, I've recently had some time to explore new directions that we can move our front-end architecture towards. I wanted to consolidate and share some of the things we've learned from our initial explorations, and document what we're considering to proceed.

### Motivation

Our current stack is built around AngularJS, as it was originally scaffolded and built in 2013, and that has held up very well for us since. However, with a breadth of new options that could potentially help us develop products faster with higher levels of confidence that things are working as intended, we decided it was worth investing in some research and exploration for what could be next.

Here are some of the complaints that our developers have had about our current stack:

- Unit test coverage is poor
  - It's difficult to write unit tests
    - You have to mock many modules that feel very unrelated
    - Writing unit tests requires relatively good understanding of the Angular digest and compile cycle, which isn't normally isn't necessary
  - Unit tests run slowly
- It's difficult to understand how data is being changed. In other words, it's hard to understand the contracts between different components.
- Components don't feel like the atomic unit in Angular, which generally leads to tightly-coupled code

### Goals

- Increase developer productivity
  - Automated testing that can help us solve problems before they happen
  - Static typing that can help us eliminate an entire class of problems
- Make it easier for new developers to get onboarded

### Non-Goals

- Using the latest and greatest
- Support for future mobile apps

### Approach

The eng team has been discussing this for a while now, and it has been tough to figure out what we wanted everything to look like (lots of bikeshedding, etc). Therefore, our team decided to just try to launch an exploratory project to see what would happen. The exploration project was an internal tool that was slated to be launched to external customers; the idea was to rebuild the internal tool and launch it, then add the bells and whistles to finish up the external one. In the end, due to delays and optimistic planning, both projects were to launch together much later than expected.

### Results

I feel like the exploratory code so far achieves all of the goals I'd want from a frontend migration. Most of the problems encountered were one-time fees to figure out how to use old code or styling that we already have set up in the new project.

Overall, I think the project is a success, and I would like to move forwards with pushing this all the way through the pipeline.

#### Wins

- For someone with some React and TypeScript experience, building things felt fairly painless
- Unit tests run fast, and it's been fairly painless to achieve relatively good code coverage (somewhere in the realm of 60-80%)
  - Minimal effort involved in getting niceities like code coverage up and running

#### Losses

- There is a _lot_ of foundational pieces that needed to be added; these components took a long time to flesh out:
  - Forms
  - Modals
  - Other misc. components (buttons, icons, etc)
  - Linking existing images and CSS
- Additional one-time costs:
  - Getting tests to run on CircleCI
  - Figuring out how to get things deployed
- Likewise, we don't have a lot of React experience period on the team, so getting code reviewed can be slow.

### Moving Forwards

#### Proposed Plan

Generally, the plan is to rebuild pages and flows one-at-a-time. Since integrating the two frameworks together on a piece-by-piece basis seems like it could work well, we can proceed like this until completion.
