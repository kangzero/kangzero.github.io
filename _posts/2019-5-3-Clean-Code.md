---
layout: post
title: Clean C/C++ Code
---

Here are some rules for clean C/C++ code with high qulity.

Some basic rules for file
==========================================================
File Declaration 
---------------------------------------------------------
Declaraion of source code file should at least incldues these basic informaiton:
1. Copyright
2. File name and abstract
3. Version number, Author or Modifier, and Date
4. Modification history

A simple templat is shown below.
```
/****************************************************************************************
    *
    * Filename: singly_linkedlist.c
    *
    * Version: v1.0
    * History:
    * V1.0     Created by Ning Kang     03/19/2019
    *
    * Copyright(c) 2019 by Ning Kang
    *
    * This software is placed into the public domain and may be used for any purpose.  
    * However, * this notice must not be changed or removed and no warranty is either 
    * expressed or implied by its publication or distribution.
    *
 ****************************************************************************************/

```
About Head Files
=========================================================
You should use preprocessor block to protect head files duplicated references.
```
#ifndef SINGLE_LINKEDLIST_H
#define SINGLE_LINKEDLIST_H

// ... ...

#endif
```
Duplicated references means a head file might be included for multiples times. Generally, this error caused by nested #include. For exmaple:

\#error
==========================================================
The purpose of \#error is to check some inconsistent behaviors during pre-processing stage.
```
#if defined(DEBUG) && define(NO_DEBUG)  
#error DEBUG and NO_DEBUG all defined!  
#endif 
```

extern "C"
==========================================================
extern "C" explictly specified compiler should build and link the codes in the block as C language, despite it is C++ syntax. 
```
#ifdef __cplusplus
extern "C" {
#endif

    void test(int a, int b);

#ifdef __cplusplus
}
#endif
```
Because C++ support function overload but no for C, thus the function name would be \_test in symbol table after build by C compiler, and it is \_test_int_int by C++ compiler. With extern "C", compiler will deal with this function as C language, then in C codes we could call C++ functions. 

Diff between <> and ""
============================================================
#include <xxx.h> 
#include "xxx.h"
<>:standard lib
"":user lib


