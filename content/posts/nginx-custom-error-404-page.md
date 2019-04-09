---
title: "How to create custom Nginx error pages for 404s"
date: 2017-11-04T10:44:02-04:00
draft: false
description: "How to create custom Nginx error pages for 404s"
tags: [nginx]
---

How to create custom Nginx error pages for 404s


nginx.conf:
```
error_page 404 /404.html;
```
