---
title: "How to Forward a Port to Different IP using \"nc\""
date: 2019-04-11T15:38:05-04:00
draft: false
description: "a useful unix networking tool"
tags: [unix,tools]
---

For example, this will redirect all TCP connections to the local port 8001 to port 80 on IP 1.1.1.1
```
nc -l -p 8001 -c "nc 8.8.8.8 80"
```

