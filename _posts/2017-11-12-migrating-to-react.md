---
layout: post
title: "Migrating from Angular to React"
date: 2017-11-12
permalink: /migrating-from-angular-to-react
---

At Color, I've recently had some time to explore new directions that we can move our front-end architecture towards. I wanted to consolidate and share some of the things we've learned from our initial explorations, and document what we're considering to proceed.

## Motivation

Our current stack is built around AngularJS, as it was originally scaffolded and built in 2013, and that has held up very well for us since. However, with a breadth of new options that could potentially help us develop products faster with higher levels of confidence that things are working as intended, we decided it was worth investing in some research and exploration for what could be next.

Here are some of the complaints that our developers have had about our current stack:

- Unit test coverage is poor
  - It's difficult to write unit tests.
    - You have to mock many modules that feel very unrelated
        - Directive templates
        - Every single service that could be opened
            - Services are also mocked in a very bizarre dangling global variable + `beforeEach` cycle.
    - Writing unit tests requires relatively good understanding of the Angular digest and compile cycle which isn't really necessary normally.
  - Unit tests run slowly.
    - Because Angular compiles directives into DOM elements, testing requires a browser instance (e.g. headless Chrome, PhantomJS, etc), which introduces a lot of lag*.
  - We make changes to products quickly, and so adding unit tests sometimes feels like a burden, especially if the behavior that you're testing may change soon.
- It's difficult to understand how data is being manipulated and transformed because any directive with a reference to some structure can mutate it. In other words, it's hard to understand the contracts between different components.
- Newer versions of Angular have some support for component-based architecture, but in general, components just don't feel like the atom in Angular.
- Directives have global namespacing.
- Despite significant improvements adding `webpack`, `babel` transforms, etc in the tooling, compiles and changes are still slow.

## Goals

- Increase developer productivity
  - Automated testing that can help us solve problems before they happen
  - Static typing that can help us eliminate an entire class of problems
- Make it easier for new developers to get onboarded
- Improve site speed*
- Use reusable components as the atoms of our frontend*
- Scoped and scaled CSS*

## Non-Goals

- Support for future mobile apps*
- Using the latest and greatest

## What's Been Done

The exploration project was rebuilding a currently internal-only tool, and then adding some finishing touches to prepare it for an external launch. It is still in progress.

### Wins

- I feel that I've been able to build things _much_ faster.
- Unit tests run very quickly, and it's been fairly painless to achieve relatively good code coverage (somewhere in the realm of 60-80%).
  - Minimal effort involved in getting niceities like code coverage up and running

### Losses

- Some problems related to attempting to have typing that is _too_ precise wasted a decent chunk of my time (particularly work on serialization types).
- There is a _lot_ of small foundational components that I didn't anticipate having to add, and each of these takes up a significant amount of time.
  - Forms
  - Modals
  - Other misc. components (buttons, icons, etc)
  - CircleCI tests
  - Deploy
  - Thankfully, these are more-or-less one-time fees.
- Some difficulties trying to figure out how to link existing
- I don't consider myself an expert in React, so I've felt like I've carved out more than I could eat in setting a lot of these structures and patterns up.
- Likewise, we don't have a lot of React experience period on the team, so getting code reviewed can be slow.

### Results

I feel like the exploratory code so far achieves all of the goals I'd want from a frontend migration. Most of the problems encountered were one-time fees to figure out how to use old code or styling that we already have set up in the new project.

My coworker hasn't had time to get onboarded, so I'm not sure if this productivity will easily translate to someone who is new to these technologies.

## Moving Forwards

### Proposed Plan

Generally, the plan is to rebuild pages and flows one-at-a-time. Since integrating the two frameworks together on a piece-by-piece basis seems like it could work well, we can proceed like this until completion.

If this is the case, I think it'd be prudent to block off some chunk of time to rebuild flows. I'd venture an extremely rough guess at ~200 hours of dev time to completely convert our team's frontend application (roughly two weeks of Justin and I working on it) after some of the aforementioned foundational blocks mentioned are completed.

### Open Questions

- What do others think of the results?
- Are there other things that haven't worked as well?
- How does the work done here stack up against other projects that need to be done soon? Does the time cost feel fair?
  - If it feels expensive, what's the right way to move frontend forwards? So far, it doesn't seem like letting people make changes on the side is making enough progress.
- How will this translate to other web apps? Does this plan work well?
