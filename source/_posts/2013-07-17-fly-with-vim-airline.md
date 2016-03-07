---
comments: true
layout: post
title: 'Fly with vim airline'
date: 2013-07-17 16:41:20
comments: true
categories:
- Vim
tags:
- Vim
---

I recently replaced my [vim-powerline][1] with [vim-airline][2]. I like vim-airline so much that
I can't help spreading words about it.

For those who don't know what vim-powerline is. It is a Vim plugin that can make the statusline of
Vim colorful and eye candy. When vim-powerline first came out, it caught on very quickly. The author
of vim-powerline even re-wrote it in Python (the project [powerline][3]) to make it work for more
applications (zsh, Tmux, ipython to name a few). But the current problems are

1. vim-powerline is deprecated. No feature is added. To support other plugins, extra work needs to
   be done (see [linepower][4])

2. powerline is too heavy for Vim users who believe *less is more*. Its dependency in Python
   complicated the installation and uninstallation. I've never set it up successfully. Most
   importantly, it is unstable. Many issues are open.

I really appreciate the hard work done by the author of vim-powerline. If vim-airline didn't appear,
I would continue to use this plugin.

Comparing with the former two, vim-airline is lightweight, vimscript-only and actively maintained.
It supports many plugins and the number is increasing. I did a very rough statistics on lines of
code:

    vim-airline:   935 lines
    vim-powerline: 2638 lines
    powerline:     11067 lines

It is impressive that vim-airline uses less than half the code of vim-powerline and all the features
are covered. Here is my settings in `.vimrc`

    """"""""""""""""""""""""""""""
    " airline
    """"""""""""""""""""""""""""""
    let g:airline_theme             = 'powerlineish'
    let g:airline_enable_branch     = 1
    let g:airline_enable_syntastic  = 1

    " vim-powerline symbols
    let g:airline_left_sep          = '⮀'
    let g:airline_left_alt_sep      = '⮁'
    let g:airline_right_sep         = '⮂'
    let g:airline_right_alt_sep     = '⮃'
    let g:airline_branch_prefix     = '⭠'
    let g:airline_readonly_symbol   = '⭤'
    let g:airline_linecolumn_prefix = '⭡'

To view the unicode glyphs correctly, please use the font patched by `fontpatcher` in the github
repo of [vim-powerline][1] (NOT POWERLINE).

Another tip. If you start Vim but the statusline is blank like this ![alt][5]
You may check in your .vimrc if you

    set lazyredraw

Comment it. You will see ![alt][6]

I strongly recommend this great plugin.


[1]: https://github.com/Lokaltog/vim-powerline
[2]: https://github.com/bling/vim-airline
[3]: https://github.com/Lokaltog/powerline
[4]: https://github.com/zhaocai/linepower.vim)
[5]: https://dl.dropboxusercontent.com/u/309872/blog/vim_lazyredraw_on.png
[6]: https://dl.dropboxusercontent.com/u/309872/blog/vim_lazyredraw_off.png
