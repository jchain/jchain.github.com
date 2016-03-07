---
layout: post
title: 'Vim gets slow when editing LaTeX file'
date: 2012-12-26 04:10
comments: true
categories: 
- Vim 
---

Recently I have been working on editing multiple LaTeX files containing many lines and equations.
I noticed there was an annoying slowdown when I moved the cursor around. CPU usage jumped to 100% so
frequently that I almost lost patience to focus on the writing itself. 

After tweaking the Vim plugins and configurations for a while, I found out `set cursorline` and the
built-in plugin `MatchParen` made Vim scrolling very slow. Some people seemed to have run into the
same problem as mentioned [here][1] and [here][2]. Some complained that Vim got slow when editing
Ruby file. And I use Vim in terminal.

I have no idea why Vim drawing is so CPU expensive. At this moment I disabled the highlighting of
`cursorline` and `cursorcolumn`

    set nocursorline
    set nocursorcolumn 

I also notice that cursor movements in the equation environment was very slow partially it was
because the math equations had so many parentheses, brackets and braces. Matching pairs and syntax
highlighting easily ate a good amount of CPU cycles. So I turned off this plugin by  

    :NoMatchParen

I didn't completely disable this plugin since I found that it was useful when editing long
equations. So I didn't try this in `.vimrc`

    let g:loaded_matchparen=1

I found some other tweaks by using Vim's `:profile` command and the verbose options `vim -V
foo.bar`. They are good ways to try to analyze the slowdown.

The lesson I learned:

1. All-around syntax highlighting seems a little bit expensive in Vim. Emacs seems to beat Vim on
   this point. 
2. Use `autocmd FileType` to further tweak the performance, such as disable the
   unnecessary plugins.


[1]: http://haerench.blogspot.com/2012/12/cursorline-cursorcolumn-and-syntax.html
[2]: https://bbs.archlinux.org/viewtopic.php?id=111647
