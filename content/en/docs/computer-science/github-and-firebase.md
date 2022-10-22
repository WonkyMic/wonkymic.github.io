---
title : "GitHub and Firebase"
description : "Describing the process to get this webpage going"
lead: "How to setup this webpage"
date : 2021-05-01T08:20:00+00:00
lastmod : 2021-05-01T08:20:00+00:00
draft : false
menu:
  docs:
    parent: "computer_science"
weight : 11
toc: true
---

# Objective
A central location to host research notes.

- Simple
- Accessible
- Quick

# Design
The appeal of Static Site Generation checks the box of staying simple. Writing notes in Markdown is something I'm already familiar with. The ability to select a pre-built theme is appealing.

[Jamstack](https://jamstack.org/generators/) maintains a list of top SSGs.

## SSG Provider
|SSG|Notes|
|:--|:--|
|[Jekyll](https://jekyllrb.com/)|Default for [GitHub Pages](https://pages.github.com/). It relies on Ruby, a Language I'm not familiar with.|
|[Zola](https://www.getzola.org/)|Written in Rust. Ran into complications with the recommended GitHub Action|
|[Docusaurus](https://docusaurus.io/)|Used at work. I'd wanted to try something new.|
|[Hugo](https://gohugo.io/)|**Selected for this project**. Multiple theme support and large community. Fast.|

## Theme 
- Needs to align with research/documentation objective. 
- Neat looking dark mode.
- LayTeX / KaTeX support

|Theme|Notes|
|:--|:--|
|[Academic](https://github.com/wowchemy/starter-hugo-academic)|Multiple configuration options with a large community.|
|[Doks](https://github.com/h-enk/doks)|**Selected for this project**. I had selected this when experimenting with Zola SSG. Great Dark theme with search capability. Focused on Doks rather than the researcher.|

## Host
The repository for this [project lives in GitHub](https://github.com/WonkyMic/wonkymic.github.io) following the format that aligns with user/organization name. This gives us the option of using [GitHub Pages](https://pages.github.com/).

From Jamstack to SSG documentation there are references to [Netfly](https://www.netlify.com/). The pricing model makes it easy to get started then charges after a resource consumption limit.

If I'm going to pay someone I'm going to align with a major provider. [Google Cloud Platform](https://cloud.google.com/) and [Amazon Web Services](https://aws.amazon.com/) come to mind. I've heard good things about Google's [Firebase](https://firebase.google.com/), so that is what we're going with.