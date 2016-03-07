---
comments: true
date: 2012-06-02 22:12:54
layout: post
slug: fix-the-broken-bash-file-and-directory-name-completion-on-ubuntu-linux
title: Fix the broken Bash file and directory name completion on Ubuntu Linux
wordpress_id: 360
categories:
- Linux
tags:
- Bash
- Linux
---

I didn't remember ever since when my Bash filename and directory name completion functioned wackily. Everytime I hit 'tab' to complete a directory name, Bash didn't append the backslash nor printed out candidates (just like what it described like [here](http://ubuntuforums.org/showthread.php?t=1053832) and [here](http://timlabath.com/words/2011/05/10/ubuntu-11-04-and-broken-bash-completion/)). It drove me banana. Meanwhile, my Bash worked very well under other Linux distributions (openSUSE, CentOS). The culprit was the a Bash completion file for adobe acrobat reader under /etc/bash_completion.d/. Delete it and the problem will be solved.
