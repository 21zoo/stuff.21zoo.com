---
title: "Enable Swap on Ubuntu"
date: 2017-12-01T14:34:06-05:00
draft: false
---

Enable Swap on Ubuntu

```
sudo fallocate -l 2G /swapfile

sudo chmod 600 /swapfile

sudo mkswap /swapfile

sudo swapon /swapfile

echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab

```
