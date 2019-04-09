---
title: 'Make "go get" use ssh instead of https'
date: 2019-10-18T19:27:12-04:00
draft: false
description: "Useful e.g. when using private repos"
tags: [golang,go,ssh]
---

To make `go get github.com/user/repo` use ssh instead of https run this line:

```
git config --global --add url."git@github.com:".insteadOf "https://github.com/"
```

It will add a section to your `~/.gitconfig` file use ssh instead of https when 
you run `go get ...`, allowing you to use your ssh key to authenticate to e.g. Github and access private repos.