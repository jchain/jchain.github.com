---
comments: true
date: 2011-02-20 00:30:56
layout: post
slug: cautious-about-the-limit-of-color-number-in-perl-gd-package
title: Cautious about the limit of color number in Perl GD package
wordpress_id: 125
categories:
- Perl
tags:
- Image processing
- Perl
- tips
---

In the recent Perl hacking, I used GD package a lot to do image processing like region labeling and
border tracing. I used GD to access the pixels. I ran into a very wired bug that the region labeling
code in some cases failed to identify the regions of interest(ROIs) correctly but worked well in
other cases.

After a painful debugging I found out the culprit. If $value is used to represent the label value,
and I use $img->setPixel($x, $y, $value) to store the value. Any value bigger than 256 will be
rounded to the range from 0 to 255 by modulo operator. So the actual value in the label image won't
be over 255. This means that if you use GD image like a matrix, the value of a element of the matrix
can't be more than 255.** I think it is due to the physical limit of the colormap which essentially
can store no more than 256 colors.**

Finally, my suggestion is using **Math::MatrixReal** package.
