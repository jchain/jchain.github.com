---
comments: true
date: 2012-03-28 21:02:43
layout: post
slug: one-tip-for-jhbuild-when-make-error-is-like-this
title: One tip for jhbuild when make error is like this
wordpress_id: 338
categories:
- Linux
tags:
- GTK
---

Here is the error message I got today
*** No rule to make target `gtkcolorsel.c', needed by `libgtk_3_la-gtkcolorsel.lo'. Stop

The reason for that is because the output files from previous builds make Automake unhappy.

The solution is
enter the jhbuild shell, and do: git clean -xdf

More details from GTK+ IRC: automake does not like when files get moved around so you need to clean up the build tree and get it back into a pristine state
