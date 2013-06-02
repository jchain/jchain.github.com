---
comments: true
layout: post
title: 'Fix Neocomplcache to Support Perl Complete'
date: 2013-06-01 20:37:24
comments: true
categories: 
- Linux 
- Perl
---

I have long been jealous about the great auto-complete feature of Python in Vim. With the wonderful
plugin `[neocomplcache][1]`, once you type `.` after an object, the memeber methods will pop up. 

I want this feature for Perl when I type `->`. Actually, until today haven't I realized that
I already own at my finger tip. The answer is `neocomplcache` and `[perlomni][2]`.


quickcd
=======

A rewrite of [fuzzycd][1] in Perl. You only need to type partial directory names to change
directories. It saves you a lot of keystrokes and enhances your productivity, especially when you
navigate in many subdirectories with tricky names.

This script is inspired by [fuzzycd][1]. Big thanks to the author for sharing his/her great code.
The way of intercepting the system `cd` is genius. I recommend you to try both scripts and choose
the one you like most.

quickcd enables you to use cd with partial directory names. For example:

    $ cd box
      => Dropbox
    $ cd ok
      => Ebook

If there is more than one directory containing your cd path, you just need to type one more letter
to take you to the target folder.

```
~ $ cd D
Make a choice:
[a] Desktop  [b] Documents  [c] Downloads  [d] Dropbox
a
Desktop $
```

[1]: https://github.com/Shougo/neocomplcache.vim
[2]: https://github.com/c9s/perlomni.vim
