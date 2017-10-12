---
layout: post
title: "Let's start with a video game"
date: 2017-10-12
tags: side-project
---

As a first side project I decided to give a go at making a video game using Phaser.<!--more--> I will try to set up the environment and follow the [tutorial](http://phaser.io/tutorials/making-your-first-phaser-game) from their webpage.

I've been reading how to set up the environment and it doesn't seem straight forward, so I'll keep a guide here too.

Setting up a http server.

For that I started a yarn project
{% highlight js %}
yarn init
{% endhighlight %}

And just add the http-server
{% highlight js %}
yarn add http-server
{% endhighlight %}

Also added the scripts tag in package.json
{% highlight json %}
"scripts": {
  "start": "http-server phaser_tutorial_02"
},
{% endhighlight %}

We have the first part of the tutorial ready [http://localhost:8080/part1.html](http://localhost:8080/part1.html)

After that, following the tutorial is quite straight forward and it took me around 40 mins.

It was actually harder to include it in this page around 50 mins. And it doesn't have some nice styles yet, at least to center it.

[Here you can check the result](/games/star-collector.html)
