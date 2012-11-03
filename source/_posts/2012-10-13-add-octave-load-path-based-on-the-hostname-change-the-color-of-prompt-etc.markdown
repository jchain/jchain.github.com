---
comments: true
date: 2012-10-13 08:38:46
layout: post
slug: add-octave-load-path-based-on-the-hostname-change-the-color-of-prompt-etc
title: 'Octave: Add local repository path based on the hostname, change the color
  of prompt etc..'
wordpress_id: 406
categories:
- Octave
tags:
- Octave
---

In my everyday work I use Git to do the version control over my dotfiles. I share my .octaverc cross different computers (four different Linux machine). I also maintain a list of local M-file repos. Not all repos are available on every machine. To get rid of the warning message for missing directory every time, I wished I could add my local directories dynamically based on the hostname. I didn't know how to do so until today I found that Octave actually has the function 'uname()' for the job. Here is an example ~/.octaverc

```python
if strcmp(uname().nodename, 'zandyware')
 addpath("~/octave")
 addpath("~/share/flann/octave")
 addpath("~/octave/niftimatlib-1.2/matlab")
end

PS1 ("\\[\\033[01;31m\\]\\s:\\#> \\[\\033[0m")

function man (name)
 help (char (name))
endfunction
```

You may also notice that I changed the default color of prompt to red for better visual contrast. Also I defined a function 'man' to alias the built-in command 'help' since I'm more used to type 'man'. This tip was copied from Octave mailinglist. Hope you like today's post.
