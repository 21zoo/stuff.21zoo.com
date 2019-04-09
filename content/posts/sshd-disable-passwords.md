---
title: "Disable password access in sshd"
date: 2017-11-04T14:11:42-04:00
draft: false
tags: [ssh,sshd]
---

Disable password access in sshd

/etc/ssh/sshd_config
```
ChallengeResponseAuthentication no
PasswordAuthentication no
UsePAM no
```


