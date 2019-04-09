---
title: "Golang - Parallelize Tests"
date: 2018-09-26T09:13:06-04:00
draft: false
description: "You can run Golang tests in parallel by using `t.Parallel()`"
tags: [golang,go,linux,windows,test]
---
You can run Golang tests in parallel by calling `t.Parallel()` in the very beginning of a test function.
For example:

```
func TestRunThisInParallel(t *testing.T) {
  t.Parallel()
  // the actual test
}
```
Tests for a specific package by default are executed sequentially, but then using `t.Parallel()` a test is marked as safe for parallel execution within the test package.<br>
Only those tests marked as parallel will be executed in parallel so ideally you should mark more than one.
<br>

You can use the `-parallel` flag when running `go test` if you need more fine-grained control over the number of tests to run in parallel. It defaults to `GOMAXPROCS`.
