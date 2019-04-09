---
title: "How to set a default namespace for \"kubectl\""
date: 2018-04-20T14:40:54-04:00
draft: false
description: "Use context to set a default namespace"
tags: [kubernetes,k8s,kubectl]
---
Kubernetes uses namespaces. If you don’t specify any, it will use the default namespace.<br/>
You can use a "Context" if you want all your kubectl commands to use the same namespace.<br/>

```
$ kubectl config set-context kube-cluster-ctx --namespace=my-namespace
Context "kube-cluster-ctx" created.
```

You have to also start using the context once it’s created like so:

```
$ kubectl config use-context kube-cluster-ctx
Switched to context "kube-cluster-ctx".
```

All subsequent `kubectl` commands will run in `my-namespace`.
