---
title: "How to define multi-line strings in yaml/yml"
date: 2017-11-14T12:19:44-05:00
draft: false
tags: [yaml,yml]
---

```yaml
key: >
  a very very
  long string
```
--> `"a very very long string"`

And with literal newlines:
```yaml
key: |
  another very very
  long string
```
--> `"another very very\nlong string"`
