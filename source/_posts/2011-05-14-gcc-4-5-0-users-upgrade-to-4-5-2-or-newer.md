---
comments: true
date: 2011-05-14 06:56:58
layout: post
slug: gcc-4-5-0-users-upgrade-to-4-5-2-or-newer
title: GCC-4.5.0 users, upgrade to 4.5.2 or newer
wordpress_id: 169
categories:
- C/C++
- GCC
- Linux
- GDB
tags:
- C++
- GCC
- GDB
- Linux
---

I'm debugging a complicated C++ program this week. It used a lot of STL containers, such as
stl::map. To print the content of stl::map in GDB-7.x with Python[
pretty-printing](http://sourceware.org/gdb/wiki/STLSupport) enabled. I got error message like
[this](http://gcc.gnu.org/ml/libstdc++/2010-06/msg00128.html). My original thought was it might be
a bug in GDB, so I upgraded it to the latest version. But the error remained. Without
pretty-printing, debugging C++ program is really a PITA. So I had to stop my work at hand and
searched for solution online. After I read this [bug report](http://gcc.gnu.org/bugzilla/show_bug.cgi?id=44645), I realised that it was due to the bug in
GCC. I did a simple test as mentioned in the bug report and found out that program compiled with
GCC-4.5.0 would mess up the pretty-printing in GDB. After installing the lastest GCC-4.5.3,
everything was OK.
