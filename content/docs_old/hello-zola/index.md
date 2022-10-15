+++
title = "GitPages and Zola Static Site Generator"
date = "2022-10-02"
+++
Create a place to capture notes to share with the world.

- GitHub Example [wonkymic/wonkymic.github.io](https://github.com/WonkyMic/wonkymic.github.io)
- 

# Hosting
The documentation at [GitHub Pages](https://pages.github.com/) introduces the topic of creation and hosting of static content. When combined with [GitHub Actions](https://github.com/features/actions) the publishing process is unencumbered.

More info on this later but we will need to implement a Custom Action (`.github/workflows/main.yml`) within our project to manage our Static Site Generator (SSG).

# SSG Selection
[Zola](https://www.getzola.org/) is used for this project.

[GitHub Pages and Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll) are used by default within GitHub's workflow. Jekyll is a foundational project to the SSG space, however, it is written in Ruby. 

Using the GitHub popularity chart of SSGs at [Jamstack](https://jamstack.org/generators/) the selections bubble to the top. The article [Jekyll vs Hugo vs Gatsby vs Next vs Zola vs Eleventy](https://mtm.dev/static)(Mark Thomas Miller 2020) makes some comparisons on speed that highlight both Hugo and Zola.