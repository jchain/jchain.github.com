---
comments: true
date: 2011-12-02 23:10:49
layout: post
slug: quick-print-a-little-trick-for-gdb-setting
title: 'Quick print: a little trick for gdb setting'
wordpress_id: 296
categories:
- Linux
tags:
- GDB
- Linux
---

Today I would like to share a little trick that I have adapted and used for a while. It is for
[gdb](en.wikipedia.org/wiki/GNU_Debugger). Before your reading the rest of the post, and if you have
no idea about the customization of gdb, please read
[here](http://zandyware.wordpress.com/2011/05/25/a-must-read-for-every-gdb-learner/)

If you use gdb frequently, chances are you have to type the command 'print' or 'p' to examine the
value of variable many many times. A common case is like this: you type 'p foo' to see the value of
'foo'. It turns out that 'foo' is a pointer, and you have to type 'p *foo' again in the commandline.
Or you have to type 'ptype foo' to find out the type definition of 'foo'. Tedious. This small piece
of gdb macro to make your life easier. Every time you type 'p foo', you just scroll up the history
and type '1', 'p foo 1' shows the dereferenced value, or typing '2' gives you the type definition of
'foo'. Copy and paste into your ~/.gdbinit 

```python
define p
 if $argc == 1
   print $arg0
 else
   if $arg1 == 1
     print *($arg0)
   else
     if $arg1 == 2
       ptype $arg0
     end
   end
 end
end
document p
   Print the variable information quickly
end
```
