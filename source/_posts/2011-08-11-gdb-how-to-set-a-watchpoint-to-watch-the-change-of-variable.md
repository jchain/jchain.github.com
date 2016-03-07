---
comments: true
date: 2011-08-11 01:32:32
layout: post
slug: gdb-how-to-set-a-watchpoint-to-watch-the-change-of-variable
title: 'GDB: How to set a watchpoint to watch the change of variable'
wordpress_id: 223
categories:
- GDB
- Linux
- Dev 
tags:
- GDB
- Linux
---

Step 1: Print the address of the variable you are going to watch.
`p *your_variable `
(Suppose the address is 0x12345678
Step 2: Set watchpoint
`watch *0x12345678`
