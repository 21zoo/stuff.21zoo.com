---
title: "git push --force-with-lease"
date: 2019-05-03T18:24:54-04:00
draft: false
description: "really, use `git push --force-with-lease`"
tags: [git,tools]
---
Instead of using `git push --force` use `git push --force-with-lease`.

It will update remote references only if it has the same value as the remote-tracking branch we have locally and reduce the risk of accidentally overwriting someone else’s work. 

You can use `alias gpf='git push --force-with-lease'` to make it more convenient. Add it to your `~/.profile` so it's loaded automatically.
