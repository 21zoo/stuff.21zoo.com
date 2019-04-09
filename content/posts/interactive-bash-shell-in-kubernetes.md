---
title: "Interactive Bash Shell in Kubernetes"
date: 2019-04-11T15:43:25-04:00
draft: false
description: When you need a quick shell in your Kubernetes cluster
tags: [kubernetes,k8s,kubectl]
---

When you need a quick shell in your Kubernetes cluster:
```
kubectl run my-shell --rm -i --tty --image ubuntu -- bash
```

Warning: this will create the shell in the default namespace normally 
has resource constraints that will lead to termiantion of processes
that take up too much CPU or memory.\
If this is a problem, add `--namespace <<ns>>` where `<<ns>>` is an 
existing namespace and the shell will be created there.
