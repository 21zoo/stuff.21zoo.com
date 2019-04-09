---
title: "Install Deluge Torrent Client on Ubuntu"
date: 2018-08-16T00:25:20-04:00
draft: false
---

First, install the Deluge PPA to get the latest releases:

```
sudo add-apt-repository ppa:deluge-team/ppa
sudo apt-get update
sudo apt-get install deluge
```

To install the headless version run:

```
 sudo apt-get install deluged deluge-web deluge-console
```
then run `deluged` to start the daemon and now you can use e.g. `deluge-console` to us the command line client.

To install the GUI version run:

```
 sudo apt-get install deluge
```

and run `deluge`.