---
comments: true
date: 2011-01-20 06:14:43
layout: post
slug: how-to-quote-long-command-in-perl-system-call
title: How to quote long command in Perl system()
wordpress_id: 91
categories:
- Perl
tags:
- Perl
- tips
---

If you call external command in your Perl code with system() and your command is very long, you must want to break it into multi-line but the newline characters really get in the way.  Here is a good way, IMHO,  to make the code look neat and clean:

[sourcecode language="perl"]
# Annotate the target and landmark image
system single_line( "
 convert -background black -fill white label:'Target Landmarks' miff:- | composite -gravity north
 -geometry +0+3 - $target_with_lmk_filename $target_with_lmk_filename
");

sub single_line {
 my @strings = @_;
 foreach ( @strings ) {
 s/\n/ /g;
 s/\r/ /g;
 }
 return wantarray? @strings : $strings[0];
}

[/sourcecode]

Credit due to [http://stackoverflow.com/questions/3707262/how-can-i-quote-a-long-string-in-perl ](http://stackoverflow.com/questions/3707262/how-can-i-quote-a-long-string-in-perl)

The biggest advantage of this method over string concatenation operator "." is that it is easier to re-align your code in Vim since your command is not messed with quotation marks.
