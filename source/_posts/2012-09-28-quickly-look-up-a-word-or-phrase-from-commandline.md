---
comments: true
date: 2012-09-28 19:46:55
layout: post
slug: quickly-look-up-a-word-or-phrase-from-commandline
title: Quickly look up a word or phrase from commandline
wordpress_id: 401
categories:
- Linux
tags:
- Bash
- Linux
- tips
---

I wrote two very short Bash functions to help me quickly look up a word or phrase using
[elinks](http://elinks.or.cz/). You can use w3m as you wish but elinks shows a better layout in my
eyes.

```bash
# look up on urbandictionary.com

ub () {
 a=$@
 elinks www.urbandictionary.com/${a// /%20}
}

# look up on thefreedictionary.com
fd () {
 a=$@
 elinks www.thefreedictionary.com/${a// /+}
}
```

Usage:
    ub your_word
    fd your_word
