---
title: "Using AppEngine go112 with CloudSQL Postgres - How to set the DB URI?"
date: 2019-07-10T10:42:43-04:00
draft: false
description: ""
tags: [appengine,cloudsql,go112,postgres,dsn]
---
With the recent upgrade of AppEngine Golang from go111 to go112 you might have to change 
your database DSNs if you're using CloudSQL and want to connect using the `/cloudsql/` socket.

DB DSN format for CloudSQL Postgres and Golang go112:

\
\
```
 "user=<<USER>> password=<<PWD> host=/cloudsql/<<CONNECTION NAME>>/ dbname=<<NAME>>"

```

The instance connection name can be found on Instance Detail page of Google Cloud Console.
Make sure your AppEngine service account has at least the CloudSQL Client role.
