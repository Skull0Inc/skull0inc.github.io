---
layout: post
title: "Git Basic Commands"
description: "Git basic useful commands"
categories: [Git, DevOps]
tags: [git,devops]
---

### Git Basic Commands (reminders)

**`git remote -v`**
~~~
# View existing remotes

HTTPS
# origin  https://github.com/user/repo.git (fetch)
# origin  https://github.com/user/repo.git (push)

SSH
# origin  git@github.com:user/repo-name (fetch)
# origin  git@github.com:user/repo-name (push)
~~~

**`git remote set-url <origin> <https://github.com/user/repo2.git>`**
~~~
# Change the 'origin' remote's URL
~~~

**`git commit --allow-empty -m "some message commit w/o actual file changes"`**
~~~
# Allow to push an empty message to log
~~~

