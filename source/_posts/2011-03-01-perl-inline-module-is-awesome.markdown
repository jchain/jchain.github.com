---
comments: true
date: 2011-03-01 20:22:50
layout: post
slug: perl-inline-module-is-awesome
title: Perl Inline module is awesome
wordpress_id: 143
tags:
- C++
- Perl
---

As you might know that I'm doing some image processing with Perl and GD module. However, iterating
a whole 512x512 image, i.e. every pixels, is prohibitively slow in Perl. Here is the Inline module
to rescue. After playing around with it in several minutes, yes, only several minutes, my Perl code
with C Inline function accessing the image boosted up 10 times faster! Every Perl programmer should
check it out:
[http://search.cpan.org/~sisyphus/Inline-0.48/Inline.pod](http://search.cpan.org/~sisyphus/Inline-0.48/Inline.pod)

Edited: I would like to add a toy example here for anyone who are interested in Perl::Inline. It
shows how to call external library(GD) from Perl script.

```c
#!/usr/bin/perl
use strict;
use warnings;

print gd_test();

use Inline C => Config =>
LIBS => '-lgd';
use Inline C => <<'END_OF_C_CODE';

#include "gd.h"

/* Bring in standard I/O so we can output the PNG to a file */
#include <stdio.h>

int gd_test() {

/* Declare the image */
gdImagePtr im;

/* Declare output files */
FILE *pngout, *jpegout;

/* Declare color indexes */
int black;
int white;

/* Allocate the image: 64 pixels across by 64 pixels tall */
im = gdImageCreate(64, 64);

/* Allocate the color black (red, green and blue all minimum).
Since this is the first color in a new image, it will
be the background color. */

black = gdImageColorAllocate(im, 0, 0, 0);

/* Allocate the color white (red, green and blue all maximum). */
white = gdImageColorAllocate(im, 255, 255, 255);

/* Draw a line from the upper left to the lower right,
using white color index. */
gdImageLine(im, 0, 0, 63, 63, white);

/* Open a file for writing. "wb" means "write binary", important
under MSDOS, harmless under Unix. */
pngout = fopen("test.png", "wb");

/* Do the same for a JPEG-format file. */
jpegout = fopen("test.jpg", "wb");

/* Output the image to the disk file in PNG format. */
gdImagePng(im, pngout);

/* Output the same image in JPEG format, using the default
JPEG quality setting. */
gdImageJpeg(im, jpegout, -1);

/* Close the files. */
fclose(pngout);
fclose(jpegout);

/* Destroy the image in memory. */
gdImageDestroy(im);
}
END_OF_C_CODE
```
