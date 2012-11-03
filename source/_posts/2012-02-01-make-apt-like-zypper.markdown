---
comments: true
date: 2012-02-01 23:43:17
layout: post
slug: make-apt-like-zypper
title: Make apt like zypper
wordpress_id: 335
categories:
- Linux
tags:
- Bash
- Linux
- tips
- Ubuntu
---

[apt](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool) is one of the reasons that I like Debian/Ubuntu, but type apt-cache search, apt-cache show, apt-get install, apt-get update, apt-get upgrade is so verbose. To make life easier, I have stolen some ideas from [zypper](http://en.wikipedia.org/wiki/ZYpp) from OpenSUSE by adding the following lines into my .bashrc:

[sourcecode language="bash"]

apt() {
 if [ "$1" = "se" ]; then
 apt-cache search $2
 fi

 if [ "$1" = "if" ]; then
 apt-cache show $2
 fi

 if [ "$1" = "up" ]; then
 sudo apt-get update
 fi

 if [ "$1" = "upgrade" ]; then
 sudo apt-get upgrade
 fi

 if [ "$1" = "in" ]; then
 sudo apt-get install $2
 fi

 if [ "$1" = "rm" ]; then
 sudo apt-get remove $2
 fi
 }

[/sourcecode]

Now you can just type 'apt se', 'apt up', 'apt upgrade', 'apt in' and 'apt if' to do the similar things.
