---
title: "Configure SSH to use a Jump Host"
date: 2017-11-26T09:09:11-05:00
draft: false
tags: [ssh]
---
Configure SSH to use a Jump Host for ssh connections:

`[ Laptop ] --ssh--> [ Jump Host ] --ssh--> [ Host ]`


`~/.ssh/config`

```
Host jump-host
  User jump-host-username
  Hostname << JUMP HOST IP >>

Host host
  User host-username
  Hostname << HOST IP >>
  ProxyCommand ssh -q -W %h:%p jump-host
```
