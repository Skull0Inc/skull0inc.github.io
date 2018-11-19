---
layout: post
title: "Updating rbenv on Linux(Ubuntu)"
description: "Updating Ruby manager rbenv"
categories: [snippet,ruby-management, dev-ops]
tags: [ruby-management, snippet, system]
redirect_from:
  - /2013/04/22/
---

### Description
My rbenv needed to be updated one time and didn't know how to go about doing that process. However came across the following and
its as simple as the commands below.

> Ref: https://www.endpoint.com/blog/2015/11/03/updating-rbenv-ruby-build-on-ubuntu

~~~ bash
cd ~/.rbenv/plugins/ruby-build/
git pull
~~~
