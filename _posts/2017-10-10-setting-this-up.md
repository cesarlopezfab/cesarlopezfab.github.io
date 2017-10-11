---
layout: post
title: "Setting this up"
date: 2017-10-10
---

I decided to start a site project once again. Not sure what will be this time. What I really decided to do is to start a blog using github pages to document the steps I take during it. <!--more-->This (hopefully) will help me recall mistakes/problems I have when I decide to start a new project in the future. As one of my desired side projects was to start to write a blog this will help to kill two birds with one stone. Also I'll write this in english even if I'm a spanish speaker. I'll try to keep a spanish version too but probably won't do it in the short term.

For my future me:

Setting up this page. Expected time 5-10 minutes.

Problems found:

 - I have set up github two factor authentication to work with my company repos. I wasn't able to push the changes without configuring a personal access token. 5 mins
 - I decided to use jekyll after setting up the page.
    - Ruby version was to old (https://stackoverflow.com/questions/38194032/how-to-update-ruby-version-2-0-0-to-the-latest-version-in-mac-osx-yosemite)
      - brew was outdated
      - installed rbenv (probably too much)
          - actually it didn't work
          - it did after executing:
          echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile
          source ~/.bash_profile
          (https://gorails.com/setup/osx/10.12-sierra)
      - installed ruby 2.4.2 (seem to be the latest stable)

Sooooo after following jekyll tutorial for a while (~20 mins) I found this gold mine (http://jmcglone.com/guides/github-pages/)

TLTR: download the files. Copy most of them inside your own folder

Actual time: ~ 1 hour
