---
comments: true
date: 2011-12-15 16:48:24
layout: post
slug: indent-only-xml-file
title: Indent only XML file
wordpress_id: 305
categories:
- Vim
tags:
- Vim
- XML
---

Recently I have worked on editing XML files in Vim. These XML files are the documents of a software in DocBook style. Since they are maintained manually, the indentation is badly formatted. So before getting deeper, the very first thing to do was to re-indent the files. It turned out from a short Google search that the tools to get the job done could be:



	
  * [xmllint](http://ku1ik.com/2011/09/08/formatting-xml-in-vim-with-indent-command.html)

	
  * [xmlindent](http://xmlindent.sourceforge.net/)

	
  * [xmlformat](http://www.kitebird.com/software/xmlformat/xmlformat.html)

	
  * [tidy](http://www.qualitybrain.com/?p=37)


xmllint, xmlindent and tidy seem to remove the empty lines I left intentionally, which is bad since I want to keep them for readability. xmlformat seems to provide such options to add blank lines but I didn't have time to look into. So finally I only used 'gg=G' in Vim to format the XML file. This operation was only to indent the file without combining or removing any blank lines. That was just what I needed. 
