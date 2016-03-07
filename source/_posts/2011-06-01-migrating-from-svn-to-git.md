---
comments: true
date: 2011-06-01 15:46:51
layout: post
slug: migrating-from-svn-to-git
title: Migrating from svn to git
wordpress_id: 198
categories:
- Git
tags:
- Git
- svn
---

Our project is consider migrating from subversion to git. I'm quite happy that git can totally serve
as a svn client. You can use git to branch and merge locally and commit into svn to let other
developers know about your changes. It sounds more flexible than centralized repository like CVS and
Subversion.

After getting my hands dirty with git for a while, I'm tempted to migrate my personal repository
from subversion to git too. Even though git is a decentralized version control system but people
still need a remote backup hosting. This is where [github.com][1] sits in. Since
I want my repository kept private, [github.com][2] is not my list. Also I wish free
git hosting can offer at least 2gb space. [Bettercodes.org][3] was my previous
choice but its host is located in Ireland, the connection speed is very slow and its UI is not very
easy to use. Today I found [assembla.com][4] located in United States offers 2gb
free git hosting. I gave it a short and so far so good. The access  is very fast. It supports https
connection, much safer than bettercodes.org and my current free svn hosting.

I found this post is very helpful for svn user switching to git.
[http://www.fnokd.com/2008/08/20/mirroring-svn-repository-to-github/][5]


[1]: http://github.com
[2]: http://github.com
[3]: http://bettercodes.org
[4]: http://assembla.com
[5]: http://www.fnokd.com/2008/08/20/mirroring-svn-repository-to-github/
