---
layout: post
title: "HTML Email Zoomed In and Not Centered on Android 4.4[Fixed]"
date: "2017-04-17 03:00:10 +0100"
blog: true
author: kofi
image: /assets/images/winterxs.jpg
tag:
  - tech
  - haml
  - email templating
  - android 4.4
  - code
comments: true
description: HTML emails not rendering properly on Android 4.4. Fix for emails that are zoomed in and issue with emails not centering with extra padding and margin.
permalink: /blog/:categories/:title/
categories: Tech
---


One if the issues that has been bugging me in recent times has been how Android 4.4 seems not to be rendering email templates correctly.

Primarily build email templates using tables in haml, build with middleman and sync to mailchimp’s mandrill. Before emails go out/ pass QA, they need render correctly on if not all, the popular devices and this is done with 250ok.com’s email testing service.

First and foremost, I found that most emails still be zoomed out on android 4.4. This seems to be peculiar to all templates in which there exists a 2 column table.

**Exhibit A**

<br> <br>
![why emails appear too large on Android 4.4](/assets/images/Blog/android44issue.png)

## How I went about fixing this:
Apparently android does not support display:block on TD’s anymore (or at least now). What seems to work is to replace all TD’s in multiple columned tables with TH


Bug 2.
After getting the the email to appear in one frame on Android 4.4, it appears the images will most of the time not center. There seem to be an extra padding/margin on the left side of the template.

**Exhibit 2**
<br><br>

![Awhy emails appear off-centre in Android 4.4](/assets/images/Blog/android44issue1.png)

## How I went about fixing this:

I basically altered body in css as follows

<script src="https://gist.github.com/Tynnee/665f0398c16c15e6cc7f7b6c27dd1921.js"></script>


The changes made were basically margin: 0 !important and padding: 0 !important on body.

Note: desist from using inlining style={‘width: 600 !important’}.

This can be problematic at times.

My table typically looks like this

<script src="https://gist.github.com/Tynnee/7739a158437c6ee377e31fbd386524e5.js"></script>


*Disclaimer: These are my workaround to issue(s) I have come across. Views, comments, and constructive critisms are most welcome*
