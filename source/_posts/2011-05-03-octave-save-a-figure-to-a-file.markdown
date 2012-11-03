---
comments: true
date: 2011-05-03 18:10:44
layout: post
slug: octave-save-a-figure-to-a-file
title: 'Octave: save a figure to a file'
wordpress_id: 165
categories:
- Math
- Octave
tags:
- Math
- Octave
---

I'm playing around [Octave](http://www.octave.org) recently. As many other open-source projects, the documentation is not complete, or more precisely speaking, not friendly to new user. When I want to save a picture to the disk, the documentation tells me to use _print()_, but I still need to try several times before get it straight. Here is my example.

[sourcecode language="matlab"]

for i=1:11
surf(x,y,ue((i-1)*0.2));
filename = sprintf("us_t%d.png", i-1);
print(filename, '-dpng'); % Note the quote
end
[/sourcecode]

BTW: I'm very grateful for the high compatibility of Octave code with Matlab code.
