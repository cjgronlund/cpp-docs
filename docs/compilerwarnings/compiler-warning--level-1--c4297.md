---
title: "Compiler Warning (level 1) C4297"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "error-reference"
f1_keywords: 
  - "C4297"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4297"
ms.assetid: ba92fcdc-9f70-4f60-abe6-281f9582ca59
caps.latest.revision: 8
ms.author: "corob"
manager: "ghogen"
translation.priority.ht: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# Compiler Warning (level 1) C4297
'function' : function assumed not to throw an exception but does  
  
 A function declaration contains a (possibly implicit) `noexcept` specifier, an empty `throw` exception specifier, or a [__declspec(nothrow)](../cpp/nothrow--c---.md) attribute, and the definition contains one or more [throw](../cpp/try--throw--and-catch-statements--c---.md) statements. To resolve C4297, do not attempt to throw exceptions in functions that are declared `__declspec(nothrow)`, `noexcept(true)` or `throw()`. Alternatively, remove the `noexcept`, `throw()`, or `__declspec(nothrow)` specification.  
  
 By default, the compiler generates implicit `noexcept(true)` specifiers for user-defined destructors and deallocator functions and compiler-generated special member functions. This conforms to the ISO C++11 standard. To prevent generation of implicit noexcept specifiers and revert the compiler to the non-standard behavior of Visual Studio 2013, use the **/Zc:implicitNoexcept-** compiler option. For more information, see [/Zc:implicitNoexcept (Implicit Exception Specifiers)](../buildref/-zc-implicitnoexcept--implicit-exception-specifiers-.md).  
  
 For more information on exception specifications, see [Exception Specifications (throw)](../cpp/exception-specifications--throw---c---.md). Also, see [/EH (Exception Handling Model)](../buildref/-eh--exception-handling-model-.md) for information on how to modify exception handling behavior at compile time.  
  
 This warning is also generated for __declspec([dllexport](../cpp/dllexport--dllimport.md)) functions marked extern "C", even if they are C++ functions.  
  
 The following sample generates C4297:  
  
```  
// C4297.cpp  
// compile with: /W1 /LD  
void __declspec(nothrow) f1()   // declared nothrow  
// try the following line instead  
// void f1()  
{  
   throw 1;   // C4297  
}  
```