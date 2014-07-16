---
comments: true
date: 2011-03-28 06:47:41
layout: post
slug: wired-mingw-make-failure-problem
title: Wired MinGW Make failure problem
wordpress_id: 161
categories:
- Cygwin
tags:
- Cygwin
- MinGW
- tips
---

Today when I tried to build wxWidgets with MinGW, I kept running into this wired problem.


> process_begin: CreateProcess(....) failed.
make (e=2): The system cannot find the file specified.


The problem was solved by reading this post [http://www.allegro.cc/forums/print-thread/593750](http://www.allegro.cc/forums/print-thread/593750)

I put Cygwin bash.exe and sh.exe into Windows PATH environment variable which make MinGW Make unhappy.
