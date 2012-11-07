---
comments: true
date: 2006-12-07 04:48:47
layout: post
slug: notes-on-installation-of-turbo-c-explorer
title: Notes on Installation of Turbo C++ Explorer
wordpress_id: 13
tags:
- Delphi
---

When starting Turbo C++ Explorer, you may get an error message stating:

  1. acces violation at adress 51F515BE rtl100.bpl....

  2. error with coreide100.bpl
	
  3. designeide100.bpl

The workaround is running "regasm" from .NET v1.1 to register the missing  .NET assemblies used by
Turbo C++ Explorer IDE. Go to the C:\Program Files\Borland\BDS\4.0\Bin directory  and run

    regasm Borland.Studio.Toolsets.dll

Now you should start the IDE successfully. If you still see an error message box, saying that a
ClassId is missing or similar errors, you can solve this by registering all possible assemblies
manually.

To do this, navigate to the BDS \Bin directory in the command line and type "dir
Borland.Studio.*.tlb" to list all relevant .tlb files. Then, run "regasm" on the corresponding .dll
file for each.(see
[http://support.borland.com/entry.jspa?externalID=4102&categoryID=39](http://support.borland.com/entry.jspa?externalID=4102&categoryID=39))

OK, then you start a new project from the menu File->New..., if you are unlucky to get an exception
Class not registered, ClassID {17CD2E5A-9D11-4BB4-8030-1092F6645714}, here is a way to fix it:

Save the [fix_turbo_cpp.reg](http://zhangcheng.johnchain.googlepages.com/fix_turbo_cpp.reg) file
into your hard disk, and double click it to import itself into the Registry.(thanks Tim Lichtenberg,
see**
**[http://qc.borland.com/wc/qcmain.aspx?d=25744](http://qc.borland.com/wc/qcmain.aspx?d=25744))

