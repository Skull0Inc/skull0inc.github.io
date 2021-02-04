---
layout: post
title: "Ubuntu: changed @hostname"
description: "Ubuntu: changed my computer hostname after upgrades"
categories: [Ubuntu, Linux]
tags: [linux,ubuntu,ssh,hostname]
---

### Ubuntu: how to change computer @hostname back using 20.xx.x

After previously doing some ubuntu system upgrades (18.xx.x - 20.xx.x) and mostly switching the laptop off due to some battery/charge-port relate issues - one day I finally had to switch it on to get some much required work pushed, only to discover that my **SSH push changes were being denied**. 

**'remote: Forbidden', 'fatal: unable to access'**

So after a bit of time digging through my ~/.ssh/config, checking access keys entered into the remote repo, creating new keys and changing the repo url to something like: *url=ssh://git@..* or *url=git@ ...* I managed to get a hostname error pop up and then I realized they my hostname was now saying '@127' instead of the regular name. This hostname mismatch was causing the error for my git not being able to push because it didnt recognize the new name. So as a result I had to end up re-setting the hostname in Ubunto which goes like this:

#### Steps
1. hostnamectl (check hostname)
2. sudo hostnamectl set-hostname &lt;new_or_old_hostname&gt;
3. check with hostnamectl
4. reboot

Previously this was done editing the /etc/hostname/ &amp; /etc/hosts files.

