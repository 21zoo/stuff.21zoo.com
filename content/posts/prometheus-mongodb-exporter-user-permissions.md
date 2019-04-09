---
title: "Prometheus Mongodb Exporter - Correct DB User Permissions"
date: 2019-08-08T10:10:10-00:00
draft: false
description: "How to configure the DB user"
tags: [prometheus,mongodb]
---

When you see the error `Failed to get local.oplog_rs collection stats.` in your mongodb exporter logs,
make sure the DB user account you use has the right permissions.

```
db.getSiblingDB("admin").createUser({
    user: "mongodb_exporter",
    pwd: "password",
    roles: [
        { role: "clusterMonitor", db: "admin" },
        { role: "read", db: "local" }
    ]
})
```

And then configure the exporter to use the `mongodb_exporter` user account.