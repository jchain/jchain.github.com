---
comments: true
date: 2011-02-06 18:25:27
layout: post
slug: linux-ldd-equivalence-on-cygwin
title: Linux 'ldd' equivalence on Cygwin?
wordpress_id: 123
tags:
- Cygwin
- Octave
- tips
---

Run "cygcheck " and see if all DLLs it requires can be found. I used it on Cygwin to solve a shared library missing problem when I started octave. The lapack library(.dll) was not loaded because of its path was not in $PATH. 
