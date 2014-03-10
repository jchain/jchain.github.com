---
comments: true
layout: post
title: 'Use Juniper VPN Client under Fedora 20 x86-64'
date: 2014-03-10 15:59:00
comments: true
categories:
- Linux
tags:
- Linux, VPN
---

This is my first time to use Juniper VPN to connect to the workplace from home. My computer runs
Fedora 20 in 64bit and Firefox in 64bit. I had a hard time to establish a connection through the web
portal. The client files were downloaded into

    ~/.juniper_networks

I followed the instructions listed [here][1], [here][2], [here][2] and [here][4]. None of them
worked. I got stuck by the error message in `ncsvc.log `like this:

    ncapp.error Failed to authenticate with IVE.

Finally this [blog post][5] saved my day. I confirmed it solved my issue. It turns out sometimes you
have to use the web browser to make the connection. Here is what I did.

1. Install 32bit Opera
2. Install 32bit JRE. Java plugin is stored in `/usr/java/default/i386/libnpjp2.so`
3. Type `about:plugins` in the address windows of Opera to find out where the plugins is located. In
   my case it is in `/usr/lib/mozilla/plugins` .
4. Made a symbolic link of 32bit Java plugin to `/usr/lib/mozilla/plugins` .
5. Re-visit the VPN login portal to set up the connection.

You should see the VPN session window pop up and the connection is up. This is the simplest way to
make everything work.

[1]: http://tuxdna.wordpress.com/2013/07/04/juniper-networks-vpn-from-fedora-17-x86_64/
[2]: https://github.com/rthill/jvpn
[3]: http://clune.org/juniper_linux.html
[4]: http://www.scc.kit.edu/scc/net/juniper-vpn/linux/
[5]: http://techydodo.wordpress.com/2012/01/17/cracking-the-juniper-network-connect-problem-on-linux-64-bit/
