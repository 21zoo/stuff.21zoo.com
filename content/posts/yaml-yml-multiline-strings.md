---
title: "How to define multiline strings in yaml/yml"
date: 2017-11-14T12:19:44-05:00
draft: false
tags: [yaml,yml]
---

```
key: >
  a very very
  long string
```
--> `"a very very long string"`

And with literal newlines:
```
key: |
  another very very
  long string
```
--> `"another very very\nlong string"`
