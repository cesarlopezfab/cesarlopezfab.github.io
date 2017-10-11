---
layout: post
title: "Jekyll first steps"
date: 2017-10-11
tags: jekyll
---


The next step after setting up the blog is to style it a little bit to avoid having plain html styles. For that I believe I should learn a little bit more of Jekyll.
<!--more-->
Right now it looks like this:
![Unstyled blog]({{ "/assets/unstyled-blog.png" | absolute_url }})

And actually the real problem was that I was missing the css file:
![css not found]({{ "/assets/css-not-found.png" | absolute_url }})

I think I'll have to look for a nicer style anyway but for the moment is fine.

Estimation: 30 mins

Real time, kind of 30 mins. 15 mins until I looked at the console and show the error :D

But I learnt

- how to add images,
- use excerpts
- and add code code snippets

{% highlight ruby linenos %}
def show
  @widget = Widget(params[:id])
  respond_to do |format|
    format.html # show.html.erb
    format.json { render json: @widget }
  end
end
{% endhighlight %}

Resources:

[Jekyll doc on posts](https://jekyllrb.com/docs/posts/)
