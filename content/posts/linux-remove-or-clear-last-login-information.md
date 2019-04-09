---
title: "Remove or Clear Last Login Information on Linux"
date: 2017-12-06T11:57:10-05:00
draft: false
---
In particular, the information returned by `lastlog` and `last`/`lastb`

```
# for lastlog

rm -f /var/log/lastlog && touch /var/log/lastlog


# for last/lastb

rm /var/log/wtmp && touch /var/log/wtmp
rm /var/log/btmp && touch /var/log/btmp

```