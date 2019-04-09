---
title: "How to get the SSL cert expiration date from PEM file"
date: 2018-04-17T16:29:54-04:00
draft: false
---
How to get the the SSL cert expiration date from PEM file

```
openssl x509 -enddate -noout -in << pem file name >>
```