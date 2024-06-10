---
title: How to Deploy a Jekyll Site with Vercel
tags: [jekyll, ruby]
categories: [日常随笔]
date: 2024-03-01 15:11:14
description: How to Deploy a Jekyll Site with Vercel
articleGPT: How to Deploy a Jekyll Site with Vercel
---

> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [vercel.com](https://vercel.com/guides/deploying-jekyll-with-vercel)

> Learn how to create a Jekyll website and deploy it live with Vercel in only a few steps.

This guide will show you how to deploy a Jekyll site and get your domain set up.

[Jekyll](https://jekyllrb.com/) is a blog-aware, static site generator perfect for personal, project, or organization sites. To build an Jekyll site, start with a template:

*   [Jekyll](https://vercel.com/new/clone?s=https%3A%2F%2Fgithub.com%2Fvercel%2Fvercel%2Ftree%2Fmain%2Fexamples%2Fjekyll&template=jekyll&id=67753070&b=main&from=templates)

[Deploy Jekyll to Vercel](#deploy-jekyll-to-vercel)
---------------------------------------------------

Vercel is a platform for deploying the fastest Jekyll sites. You can deploy your site with zero configuration to the best [frontend infrastructure](https://vercel.com/features/infrastructure).

*   **Develop:** Build Jekyll sites that connect to your favorite APIs, databases, and content management systems.
*   **Preview:** Integrate with any GitHub, GitLab, or Bitbucket repository for [instant continuous deployment](https://vercel.com/features/previews).
*   **Ship:** Deploy your site to every edge node worldwide for the fastest Jekyll sites. Static files, Serverless and Edge Functions, and [more](https://vercel.com/features/infrastructure).

[Built-in CI/CD for Jekyll sites](#built-in-ci/cd-for-jekyll-sites)
-------------------------------------------------------------------

Vercel has integrations for [GitHub](https://vercel.com/docs/deployments/git/vercel-for-github), [GitLab](https://vercel.com/docs/deployments/git/vercel-for-gitlab), and [Bitbucket](https://vercel.com/docs/deployments/git/vercel-for-bitbucket) to enable CI/CD for your Jekyll site with zero configuration. Then, you can run [automated tests for performance and reliability](https://vercel.com/docs/concepts/deployments/checks) on every push. Pull and merge requests are deployed instantly to a unique URL, accessible to your entire team.

[Add your custom domain](#add-your-custom-domain)
-------------------------------------------------

After deploying, your new Jekyll site will get automatically assigned a `.vercel.app` suffixed domain. You can then add a [Custom Domain](https://vercel.com/docs/concepts/projects/custom-domains) on your choice, either from a third-party or [purchased through Vercel](https://vercel.com/domains).

[Deploy Jekyll to Vercel](#deploy-jekyll-to-vercel)
---------------------------------------------------

### [Start from a template](#start-from-a-template)

*   [Jekyll](https://vercel.com/new/clone?s=https%3A%2F%2Fgithub.com%2Fvercel%2Fvercel%2Ftree%2Fmain%2Fexamples%2Fjekyll&template=jekyll&id=67753070&b=main&from=templates)

### [Vercel CLI](#vercel-cli)

1.  Install the [Vercel CLI](https://vercel.com/cli) and run `vercel` to deploy.
2.  Vercel will detect that you are using Jekyll and will enable the correct settings for your deployment.
3.  Your site is deployed! (e.g. [jekyll-template.vercel.app](https://jekyll-template.vercel.app/))

### [Vercel for Git](#vercel-for-git)

1.  Push your code to your git repository (GitHub, GitLab, BitBucket).
2.  [Import your Jekyll project](https://vercel.com/new) into Vercel.
3.  Vercel will detect that you are using Jekyll and will enable the correct settings for your deployment.
4.  Your site is deployed! (e.g. [jekyll-template.vercel.app](https://jekyll-template.vercel.app/))

[Caveats](#caveats)
-------------------

Please note that recent `Bundler` versions (2.2.3+) started changing the way of deciding the installing platform (more details in this GitHub [issue](https://github.com/rubygems/rubygems/issues/4269)). Therefore, please run the following command locally in your project repository once, and commit the resulting `Gemfile.lock` file to be able to deploy your project on Vercel:

```
bundle lock --add-platform x86_64-linux
```

This is important especially if you're developing your app on different platforms (e.g., macOS, Windows, etc) as Vercel's build environment uses Linux.