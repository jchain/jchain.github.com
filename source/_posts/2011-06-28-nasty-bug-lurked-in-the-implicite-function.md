---
comments: true
date: 2011-06-28 18:16:51
layout: post
slug: nasty-bug-lurked-in-the-implicite-function
title: Nasty bug lurked in the implicite function
wordpress_id: 210
categories:
- C/C++
- Linux
tags:
- C/C++
- GCC
- Linux
---

I fixed a bug in C code today and it was so nasty that I think it is worth a blog post so that I can keep that in mind.

I called a function which allocated a chunk of memory with malloc() and returned a pointer pointing to that memory. The wired thing is the returned address will change so that the caller get an invalid address(out of the bound of memory). More precisely speaking, the most significant bit changes from 0x7fff.... to 0xffff.... I really had no clue about why it would go like that. I even tried to disassemble the C code to check what was wrong. It turned out that the return address in the callee was correct but after returning the address to the caller, the value changed. I wrote another toy program to verify everything and finally I nailed down the reason. The callee function is defined in another C file and it looks like an implicit function to the caller. Somehow, this implicit function changed the address during the call. The compilation was fine even though GCC threw a warning about it. I ignored it at the first place but eventually this warning bit me. After adding necessary definitions in the header files. My program worked like a charm.

The lesson I learned: don't ignore the warning messages of compiler.
