---
comments: true
date: 2011-10-21 06:50:36
layout: post
slug: octave-plot-legend-fontsize
title: Octave plot legend fontsize?
wordpress_id: 257
categories:
- Octave
tags:
- Octave
---

I wanted to create a line plot in Octave today and saved it as a eps file. But no matter how hard I tried I simply couldn't change the font size of the plot legend. It was too small in my document. There is already much discussion about it on the web. No tricks worked for me. Finally I realized that what I really cared about was the font size in file output not the gnuplot screen output. So I just tried '**print('foo.eps','-depsc','-F:14')**'. The option '-F:14' set the default print fontsize to 14. It worked so far so good.
