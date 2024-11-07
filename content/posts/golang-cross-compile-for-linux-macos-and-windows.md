---
title: "Golang Cross Compile for Linux Macos and Windows"
date: 2018-04-19T13:29:05-04:00
draft: false
tags: [golang,go,linux,windows,test]
---

For Linux desktop:
```shell
$ GOOS=linux GOARCH=amd64 go build
```

For MacOS:
```shell
$ GOOS=darwin GOARCH=arm64 go build
```

For old Windows desktop:

```shell
$ GOOS=windows GOARCH=386 go build
```