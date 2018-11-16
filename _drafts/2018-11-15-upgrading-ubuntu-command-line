---
layout: post
published: true
title: "Upgrading Ubuntu"
description: "Upgrading Ubuntu command line"
categories: [Rails]
tags: [ajax, rails]
redirect_from:
  - /2018/11/15/
---

> Quick Overview:
  1. Open 

* Kramdown table of contents
{:toc .toc}
> Notes taken from https://www.zdnet.com/article/how-to-upgrade-to-ubuntu-linux-18-04/

##### Steps 
* nodejs 
   
   (optional)
   add-apt-repository -y -r ppa:chris-lea/node.js
   rm -f /etc/apt/sources.list.d/chris-lea-node_js-*.list
   apt-get update
   > Mainly the above nodeJS stuff is because of version difference when using Mina deployment.

  * sudo apt dist-upgrade
  * sudo apt autoremove
  * sudo apt-get install update-manager-core
  * sudo vim /etc/update-manager/release-upgrades
  * sudo do-release-upgrade -d

