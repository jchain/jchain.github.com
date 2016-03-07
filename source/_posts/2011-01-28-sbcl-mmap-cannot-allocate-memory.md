---
comments: true
date: 2011-01-28 19:28:53
layout: post
slug: sbcl-mmap-cannot-allocate-memory
title: sbcl mmap cannot allocate memory?
wordpress_id: 117
categories:
- Lisp
tags:
- Common Lisp
- tips
---

Recently I want to give Common Lisp a try. After reading this great [Common Lisp Implementation Survey](http://common-lisp.net/~dlw/LispSurvey.html), I decided to go first with SBCL. After installing the binary package of SBCL-1.0.45 on my openSUSE-11.1 x86-64bit with 8Giga memory, I ran into this annoying error message when I started SBCL in terminal:


> mmap: Cannot allocate memory
ensure_space: failed to validate 8589869056 bytes at 0x1000000000
(hint: Try "ulimit -a"; maybe you should increase memory limits.)


I researched online for a while and finally I came up a solution(it worked for me at least). Solution: start sbcl like this


> sbcl --dynamic-space-size 2028 --core /local/vol00/software/lib/sbcl/sbcl.core


I guess the reason to fail is that by default sbcl will allocate 8Giga MB memory on x86-64 bit platform, which is not permitted due to the physical memory limitation. So use --dynamic-space-size to change the setting, also use --core option if your sbcl installation is not in the default location.
