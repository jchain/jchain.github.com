---
comments: true
date: 2011-11-09 04:23:38
layout: post
slug: gnuplot-how-to-skip-the-first-line-in-the-data-file
title: 'Gnuplot: how to skip the first line in the data file'
wordpress_id: 277
tags:
- Gnuplot
- tips
---

It is very likely that the data file you are going to visualize has a one line header at the first
line. Use 'every' keyword to skip the first line like this.

    plot "foo.dat" every ::1 using 1:2 with lines

Similarly you can skip 2 or 3 or whatever lines using 'every'
