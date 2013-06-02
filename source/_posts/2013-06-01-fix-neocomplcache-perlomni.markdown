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
plugin [`neocomplcache`][1], once you type `.` after an object, the memeber methods will pop up. 

I want this feature for Perl when I type `->`. Actually, until today haven't I realized that
I already own at my finger tip. The answer is `neocomplcache` and [`perlomni`][2].

The installation of `neocomplcache` and `perlomni` is easy. If you use the settings from the help of
`neocomplcache`, the key part to triger `neocomplcache` omni-complete by `->` is to change the
setting in `.vimrc` from  

    let g:neocomplcache_omni_patterns.perl = '\h\w*->\h\w*\|\h\w*::'

to

    let g:neocomplcache_omni_patterns.perl = '\h\w*->\|\h\w*->\h\w*\|\h\w*::\|\h\w*::\h\w*'

Make sure `omnifunc` is `PerlComplete`.

A little explanation: `\h\w*->` will triger the popup window, `\h\w*->\h\w*` will complete
as-you-type. The similar situation goes to `::` operator. But do remember that sometimes `::` won't
triger neocomplcache if the package is not based on the OO that perlomni supports. In this case,
`C-X C-O` will always pop up the window.  After this you should see someting like this:

![alt](https://dl.dropboxusercontent.com/u/309872/blog/2013-06-01-perlomni-in-vim.png)

[1]: https://github.com/Shougo/neocomplcache.vim
[2]: https://github.com/c9s/perlomni.vim
