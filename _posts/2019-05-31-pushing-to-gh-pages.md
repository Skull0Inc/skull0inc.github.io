---
layout: post
title: "How to properly push to gh-pages branch"
description: "Properly psuhing to gh-pages branch"
categories: [GitHub, Blog]
tags: [gitgub,github-pages,blog]
---

### GitHub Pages, how to properly push to gh-pages branch for markdown blog.

Firstly make sure that the selected branch on GitHub is set to **gh-pages** for the repo.

At some stage I managed to be on the master branch when making a new post. I made all the changes to the post I wanted to and pushed as usual.
However I ran into the issue of the ssh-agent not detecting the correct ssh-key and the password being input was always wrong. Something was wrong. Usually this happends when the ssh-agent isnt finding the correct key for the online repo.


#### If the private key hasn't been added to ssh-agent keychain

In case the correct ssh key hadn't been added correctly to **ssh-agent** use `ssh-add` `<key-file-name>` usually located in `~/.ssh`. Type in the password for the key so that the passphrase isn't requiested all the time.

#### Create gh-pages branch, merge it with master commit and push
I pushed my changes to **master** and realized that the **gh-pages** branch and therefore the blog was not updated. Not good.

What happened next was to do the following:

~~~bash
git checkout gh-pages
git merge master
git commit -am 'initial gh-pages update'
git push
~~~

With the above done, I'm now able to correctly push to my gh-pages branch.
