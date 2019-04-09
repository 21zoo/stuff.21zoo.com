---
title: "Bash Shell - Append Date to Filename"
date: 2017-11-14T10:49:28-05:00
draft: false
---

Append the current date to a filename in Bash shell:

```
$ fname="/var/log/output-$(date +"%Y-%m-%d").log"
$ echo $fname
/var/log/output-2017-11-14.log
$
```

