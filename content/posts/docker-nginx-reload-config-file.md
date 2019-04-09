---
title: "Reload Nginx config inside a Docker container"
date: 2019-05-20T15:10:12-04:00
draft: false
description: "A useful way to avoid downtime"
tags: [docker,nginx]
---

Check the new configuration:

```
$  docker container exec <<< container name >> nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
$
```


Apply the new configuration:

```
$  docker container exec <<< container name >> nginx -s reload
2019/05/20 19:14:29 [notice] 7#7: signal process started
$
```




