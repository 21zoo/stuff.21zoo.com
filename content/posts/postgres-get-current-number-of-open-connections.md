---
title: "Postgres - Get the Current Number of Open Connections"
date: 2019-07-12T14:28:47-04:00
draft: false
description: "metrics"
tags: [postgres,postgresql,sql]
---

Get the Current Number of Open Connections for a Postgres DB:

```
SELECT * FROM pg_stat_database;
```