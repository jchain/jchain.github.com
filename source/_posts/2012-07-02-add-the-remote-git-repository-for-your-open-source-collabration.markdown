---
comments: true
date: 2012-07-02 00:39:25
layout: post
slug: add-the-remote-git-repository-for-your-open-source-collabration
title: Add the remote git repository for your open-source collabration
wordpress_id: 364
categories:
- Git
tags:
- git
---

When I hacked on github I would clone the upstream repository FOO into my local disk creating a 'master' branch. I hacked there and formatted a patch to the upstream repo owner. But I quickly found the need that I wanted to have my github-hosted 'master' branch since I wanted my local hack could be backed up and synced online. So I changed my workflow. For any git project I was interested to hack I would create a new cloned repo my_FOO from the original on github under my owership. Then I git clone this my_FOO/master(origin/master) into a local branch 'master' and I would hack under this branch.

But after my hack right before I fire up the 'git format-patch' command, I would like to have  a updated upstream master branch available so that I can format my patch to the latest code base. Also I would like to update the code from the upstream everyday to keep tracking the latest changes. The command 'git remote' will help. I found a good documentation on this issue. Check it out [here](http://gitref.org/remotes/).

Here is a short summary:



	
  1. Suppose the original project is called FOO. We create a new repo called my_FOO by imported the code from the git repo of FOO

	
  2. git clone git://git.github.com/my_FOO.git. You will have a local master branch

	
  3. git remote add FOO_origin git://git.github.com/FOO.git. You will add a new remote repo in your .git/config

	
  4. git fetch FOO_origin. You have to do this to get the branch information about FOO_origin before step 5.

	
  5. git branch --set-upstream FOO_master FOO_origin/master. Create a local branch named FOO_master to keep track the upstream's master branch.

	
  6. Done. use 'git branch' to check the result.


OK. After these steps, you can code in the 'master' branch, commit and push to the repo 'my_FOO' for the benefit of online backup and sync. You can switch to FOO_master to pull the upstream changes and merge to your 'master' branch. When you feel ready to format a patch, just type 'git format-patch FOO_master'.

Of cause there are issues like commit squash but that is another topic so I don't mention here. I'm surprised to see there are tons of git questions flying around on the web. After all git is really a complicated tool with a much higher learning curve than Subversion. For some particular use cases I find it make sense to blog them here for my own future reference instead of searching online but retrieved a lot of partially related answers.
