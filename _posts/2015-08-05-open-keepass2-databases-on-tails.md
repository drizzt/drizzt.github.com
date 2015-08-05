---
layout: post
title: "Open KeePass2 databases on Tails"
description: ""
category: 
tags: []
---
{% include JB/setup %}

If you want to create or open [KeePass2](http://keepass.info/) databases on [Tails](https://tails.boum.org/) you have 3 ways:

1. You can install the keepass package, using the experimental feature of [Additional software packages](https://tails.boum.org/doc/first_steps/persistence/configure/index.en.html#index14h2).
2. You can compile the last version of [keepassx](https://www.keepassx.org/) 2
3. You can use my [precompiled](https://gist.github.com/drizzt/478999e752dbee5148bd#file-keepassx-run) version of keepassx2, with patches for TwoFish support.

This post is about the _third_ point (the simpler one).

If you simply want to open a KeePass2 database and you don't want to compile it by yourself or to follow experimental procedure, just use my precompiled version of keepassx.

Just point your _Tor Browser_ to [`http://git.io/keepassx4tails`](http://git.io/keepassx4tails), download the file, copy it to your Persistent Volume (optional) and launch it.  
The configuration file (`keepass2.ini`) will be created in the same directory as `keepassx.run`.
