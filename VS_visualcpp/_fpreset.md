---
title: "_fpreset"
ms.custom: na
ms.date: 10/03/2016
ms.devlang: 
  - C++
  - C
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-cpp
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - _fpreset
apilocation: 
  - msvcrt.dll
  - msvcr80.dll
  - msvcr90.dll
  - msvcr100.dll
  - msvcr100_clr0400.dll
  - msvcr110.dll
  - msvcr110_clr0400.dll
  - msvcr120.dll
  - msvcr120_clr0400.dll
  - ucrtbase.dll
  - api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
ms.assetid: f31c6a04-b464-4f07-a7c4-42133360e328
caps.latest.revision: 14
manager: ghogen
translation.priority.ht: 
  - cs-cz
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pl-pl
  - pt-br
  - ru-ru
  - tr-tr
  - zh-cn
  - zh-tw
---
# _fpreset
Resets the floating-point package.  
  
## Syntax  
  
```  
void _fpreset( void );  
```  
  
## Remarks  
 The `_fpreset` function reinitializes the floating-point math package. `_fpreset` is usually used with `signal`, `system`, or the `_exec` or `_spawn` functions. If a program traps floating-point error signals (`SIGFPE`) with `signal`, it can safely recover from floating-point errors by invoking `_fpreset` and using `longjmp`.  
  
 This function is deprecated when compiling with [/clr (Common Language Runtime Compilation)](../VS_visualcpp/-clr--Common-Language-Runtime-Compilation-.md) or `/clr:pure` because the common language runtime only supports the default floating-point precision.  
  
## Requirements  
  
|Function|Required header|  
|--------------|---------------------|  
|`_fpreset`|<float.h>|  
  
 For more compatibility information, see [Compatibility](../VS_visualcpp/Compatibility.md) in the Introduction.  
  
## Example  
  
```  
// crt_fpreset.c  
// This program uses signal to set up a  
// routine for handling floating-point errors.  
  
#include <stdio.h>  
#include <signal.h>  
#include <setjmp.h>  
#include <stdlib.h>  
#include <float.h>  
#include <math.h>  
#include <string.h>  
  
jmp_buf mark;              // Address for long jump to jump to  
int     fperr;             // Global error number  
  
void __cdecl fphandler( int sig, int num );   // Prototypes  
void fpcheck( void );  
  
int main( void )  
{  
   double n1 = 5.0;  
   double n2 = 0.0;  
   double r;  
   int jmpret;  
  
   // Unmask all floating-point exceptions.   
    _control87( 0, _MCW_EM );  
   // Set up floating-point error handler. The compiler  
   // will generate a warning because it expects  
   // signal-handling functions to take only one argument.  
   if( signal( SIGFPE, (void (__cdecl *)(int)) fphandler ) == SIG_ERR )  
    {  
       fprintf( stderr, "Couldn't set SIGFPE\n" );  
       abort();  
    }  
  
   // Save stack environment for return in case of error. First   
   // time through, jmpret is 0, so true conditional is executed.   
   // If an error occurs, jmpret will be set to -1 and false   
   // conditional will be executed.  
   jmpret = setjmp( mark );  
   if( jmpret == 0 )  
   {  
      printf( "Dividing %4.3g by %4.3g...\n", n1, n2 );  
      r = n1 / n2;  
      // This won't be reached if error occurs.  
      printf( "\n\n%4.3g / %4.3g = %4.3g\n", n1, n2, r );  
  
      r = n1 * n2;  
      // This won't be reached if error occurs.  
      printf( "\n\n%4.3g * %4.3g = %4.3g\n", n1, n2, r );  
   }  
   else  
      fpcheck();  
}  
// fphandler handles SIGFPE (floating-point error) interrupt. Note  
// that this prototype accepts two arguments and that the   
// prototype for signal in the run-time library expects a signal   
// handler to have only one argument.  
//  
// The second argument in this signal handler allows processing of  
// _FPE_INVALID, _FPE_OVERFLOW, _FPE_UNDERFLOW, and   
// _FPE_ZERODIVIDE, all of which are Microsoft-specific symbols   
// that augment the information provided by SIGFPE. The compiler   
// will generate a warning, which is harmless and expected.  
  
void fphandler( int sig, int num )  
{  
   // Set global for outside check since we don't want  
   // to do I/O in the handler.  
   fperr = num;  
  
   // Initialize floating-point package. */  
   _fpreset();  
  
   // Restore calling environment and jump back to setjmp. Return   
   // -1 so that setjmp will return false for conditional test.  
   longjmp( mark, -1 );  
}  
  
void fpcheck( void )  
{  
   char fpstr[30];  
   switch( fperr )  
   {  
   case _FPE_INVALID:  
       strcpy_s( fpstr, sizeof(fpstr), "Invalid number" );  
       break;  
   case _FPE_OVERFLOW:  
       strcpy_s( fpstr, sizeof(fpstr), "Overflow" );  
  
       break;  
   case _FPE_UNDERFLOW:  
       strcpy_s( fpstr, sizeof(fpstr), "Underflow" );  
       break;  
   case _FPE_ZERODIVIDE:  
       strcpy_s( fpstr, sizeof(fpstr), "Divide by zero" );  
       break;  
   default:  
       strcpy_s( fpstr, sizeof(fpstr), "Other floating point error" );  
       break;  
   }  
   printf( "Error %d: %s\n", fperr, fpstr );  
}  
```  
  
 **Dividing    5 by    0...**  
**Error 131: Divide by zero**   
## See Also  
 [Floating-Point Support](../VS_visualcpp/Floating-Point-Support.md)   
 [_exec, _wexec Functions](../VS_visualcpp/_exec--_wexec-Functions.md)   
 [signal](../VS_visualcpp/signal.md)   
 [_spawn, _wspawn Functions](../VS_visualcpp/_spawn--_wspawn-Functions.md)   
 [system, _wsystem](../VS_visualcpp/system--_wsystem.md)