---
layout: post
title: Install Parse Server on Ubuntu (With Dashboard)
blog: true
author: kofi
image: "/assets/images/Blog/ubersign.jpg"
tag:
- tech
- parse
- parse server
- ubuntu
- serverless
comments: true
description: How to install Parse Server Ubuntu.
permalink: "/blog/:categories/how-to-install-parse-server-on-ubuntu"
categories: Tech

---
<div class="side-by-side">
<div class="toleft">
<img class="image" src="/assets/images/Blog/parse-server.png" alt="Parse Server">
</div>

    <div class="toright">
        <p>Being a firm believer in rapid prototyping, it is important to me not to try re-invent the wheel when working on side projects. Facebook's Parse project is one of the tools in my arsenal when it comes to getting a fully functional backend up and running in no time. </p>
    </div>

</div>

<div class="breaker"></div>

It gives you out of the box a full functioning backend and a great community maintaining the source code and making it easier to get started. Good starting point is the Parse Server Example App.

![Tell me more about parse server](https://media.giphy.com/media/aGOgOKmyBxCk8/giphy.gif)

With just a few tweaks, you can get the server up with the dashboard out of the box. This will be walkthrough installing it on an ubuntu server since the boilerplate code already has one click install options for AWS, Heroku, etc.

* ssh into your server (I am assuming you are using a digital ocean droplet but it should work same on lightsail, etc)
  {% highlight raw %}
  ssh root@yourserverip
  {% endhighlight %}
* Install Node
  {% highlight raw %}
  sudo apt-get update
  sudo apt-get install nodejs
  {% endhighlight %}
* Install Mongo DB
  {% highlight raw %}
  sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2930ADAE8CAF5059EE73BB4B58712A2291FA4AD5
  {% endhighlight %}

  {% highlight raw %}
  echo "deb \[ arch=amd64 \] https://repo.mongodb.org/apt/ubuntu precise/mongodb-org/3.6 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.6.list
  {% endhighlight %}

  {% highlight raw %}
  echo "deb \[ arch=amd64,arm64 \] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.6 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.6.list
  {% endhighlight %}
* Download and Clone the repository
* cd into the repo
  {% highlight raw %}
  git clone https://github.com/BruhKofi/my-parse-server-boilerplate.git
  {% endhighlight %}
* Install Dependencies
  {% highlight raw %}
  npm install
  {% endhighlight %}
* Change the config in index js to match your server. Change local host to your server's address
* Fire Up your engines
  {% highlight raw %}
  npm start
  {% endhighlight %}

**Your server must be working now. Depending on your server, you may have to visit YourServerIP:1337/dashboard. You can log in with the username and password which is set in Index.js.__*

Now go forth and save the world

![Mind blown](https://media.giphy.com/media/3o7TKH2MQAHwqCMVgs/giphy.gif)