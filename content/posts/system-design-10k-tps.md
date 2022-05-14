+++
title = "Design a system for serving blogs to massive readers (10k tps)"
description = ""
tags = [
    "go",
    "golang",
    "hugo",
    "development",
]
date = "2022-05-13"
categories = [
    "Development",
    "golang",
]
+++

## 1. Introduction

First of all, a blog (a shortened version of “weblog”) is an online journal or informational website displaying information in reverse chronological order, with the latest posts appearing first, at the top. It is a platform where a writer or a group of writers share their views on an individual subject.

Today, there are more than 570 million blogs on the web.

**And what is the purpose of a blog?**

The main purpose of a blog is to connect you to the relevant audience. Another one is to boost your traffic and send quality leads to your website.

So to grow in the long term and connect with more people, you need a system that can handle a large and effective traffic for your blog/homepage. 

And in this blog, specific to the problem here is **10000 transactions per second (10k tps)**. 

To do that, let's work together to find solutions for your own system.

## 2. Point out the problems

After researching and asking some more experienced people, I think to build the system as mentioned above, we will encounter 2 main types of problems:
- **About product (blog):**
  - Your blog is for the purpose of reading articles only ?
  - In addition to serving articles, you are also welcome to allow your readers to send you messages or do other things such as donate ?
- **About technology:**
  - what technologies help your system achieve 10k tps ?

## Step 3. Change the docs site

Stop the Hugo process by hitting ctrl+c.

Now we are going to run hugo again, but this time with hugo in watch mode.

    /path/to/hugo/from/step/1/hugo server --source=./docs --watch
    > 29 pages created
    > 0 tags index created
    > in 27 ms
    > Web Server is available at http://localhost:1313
    > Watching for changes in /Users/spf13/Code/hugo/docs/content
    > Press ctrl+c to stop


Open your [favorite editor](http://vim.spf13.com) and change one of the source
content pages. How about changing this very file to *fix the typo*. How about changing this very file to *fix the typo*.

Content files are found in `docs/content/`. Unless otherwise specified, files
are located at the same relative location as the url, in our case
`docs/content/overview/quickstart.md`.

Change and save this file.. Notice what happened in your terminal.

    > Change detected, rebuilding site

    > 29 pages created
    > 0 tags index created
    > in 26 ms

Refresh the browser and observe that the typo is now fixed.

Notice how quick that was. Try to refresh the site before it's finished building.. I double dare you.
Having nearly instant feedback enables you to have your creativity flow without waiting for long builds.

## Step 4. Have fun

The best way to learn something is to play with it.
