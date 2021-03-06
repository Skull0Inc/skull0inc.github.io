---
layout: post
title: "Git Basic Commands"
description: "Git basic useful commands"
categories: [Git, DevOps]
tags: [git,devops]
---

### Git Basic Commands (reminders)

##### View existing remotes
```console
git remote -v
```


##### HTTPS
- origin  https://github.com/user/repo.git (fetch)
- origin  https://github.com/user/repo.git (push)


##### SSH
- origin  git@github.com:user/repo-name (fetch)
- origin  git@github.com:user/repo-name (push)

##### Change the 'origin' remote's URL
```console
git remote set-url <origin> <https://github.com/user/repo2.git>
```

##### Allow to push an empty message to log
```console
git commit --allow-empty -m "some message commit w/o actual file changes"
```

