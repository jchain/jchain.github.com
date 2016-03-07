---
comments: true
date: 2010-04-27 05:32:06
layout: post
slug: shrink-the-file-size-of-a-pdf
title: Shrink the file size of a pdf?
wordpress_id: 19
categories:
- Linux
tags:
- text processing
- tips
---

Want to shrink the file size of a pdf? Use the following command. ebook has a good balance between the file size and the image quality. screen compresses the images too much.


`gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/ebook[screen, ] -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf`



**-dPDFSETTINGS=**_configuration_
    Presets the "distiller parameters" to one of four predefined settings:



	
  * **/screen** selects low-resolution output similar to the Acrobat Distiller "Screen Optimized" setting.

	
  * **/ebook** selects medium-resolution output similar to the Acrobat Distiller "eBook" setting.

	
  * **/printer** selects output similar to the Acrobat Distiller "Print Optimized" setting.

	
  * **/prepress** selects output similar to Acrobat Distiller "Prepress Optimized" setting.

	
  * **/default** selects output intended to be useful across a wide variety of uses, possibly at the expense of a larger output file.



