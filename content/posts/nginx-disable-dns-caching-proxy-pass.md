---
title: "How to prevent Nginx from Caching DNS for Proxy Upstreams"
date: 2019-05-28T20:39:51-04:00
draft: false
description: "when your upstreams change often"
tags: [nginx]
---

Normal use of `proxy_pass`

```
server {
    proxy_pass http://upstream-host.com:8080;
}
```

Instead, use a variable in your nginx config to disable nginx caching the DNS for `upstream-host.com` like this:

```
server {
    ...
    resolver 127.0.0.1;
    set $backend "http://upstream-host.com:8080";
    proxy_pass $backend;
    ...
}
```

When nginx is running inside a Docker container then you need to use:

```
    resolver 127.0.0.11 ipv6=off;
```