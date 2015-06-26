---
layout: post
title: "Using Wireshark remotely"
description: ""
category: 
tags: [tcpdump, wireshark]
---
{% include JB/setup %}

If you want to sniff traffic remotely, but you want to have the confort of using the [Wireshark](https://www.wireshark.org/) GUI, you just have to use tcpdump piped to wireshark:

`ssh root@$remote_host tcpdump -nUs 0 -i $intf -w- | wireshark -ki -`

_$remote_host_ is the IP address or hostname of the remote machine you want to login with SSH.  
_$intf_ is the remote interface you want to sniff.
