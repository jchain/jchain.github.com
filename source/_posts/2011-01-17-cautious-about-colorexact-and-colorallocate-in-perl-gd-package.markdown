---
comments: true
date: 2011-01-17 06:33:45
layout: post
slug: cautious-about-colorexact-and-colorallocate-in-perl-gd-package
title: Cautious about colorExact() and colorAllocate() in Perl GD package
wordpress_id: 76
tags:
- Image processing
- Perl
- tips
---

For exising colors, I think it is better to use colorExact() because the color indices would be consistent among images. For new colors, colorAllocate() is the only choice. But colorAllocate() is highly recommended to use after colorExact(). It is safer to the color palette. 

