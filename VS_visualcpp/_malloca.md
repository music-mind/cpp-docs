---
title: "_malloca"
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
  - _malloca
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
apitype: DLLExport
ms.assetid: 293992df-cfca-4bc9-b313-0a733a6bb936
caps.latest.revision: 27
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
# _malloca
Allocates memory on the stack. This is a version of [_alloca](../VS_visualcpp/_alloca.md) with security enhancements as described in [Security Features in the CRT](../VS_visualcpp/Security-Features-in-the-CRT.md).  
  
## Syntax  
  
```  
void *_malloca(   
   size_t size   
);  
```  
  
#### Parameters  
 `size`  
 Bytes to be allocated from the stack.  
  
## Return Value  
 The `_malloca` routine returns a `void` pointer to the allocated space, which is guaranteed to be suitably aligned for storage of any type of object. If `size` is 0, `_malloca` allocates a zero-length item and returns a valid pointer to that item.  
  
 A stack overflow exception is generated if the space cannot be allocated. The stack overflow exception is not a C++ exception; it is a structured exception. Instead of using C++ exception handling, you must use [Structured Exception Handling](../VS_visualcpp/Structured-Exception-Handling--C-C---.md) (SEH).  
  
## Remarks  
 `_malloca` allocates `size` bytes from the program stack or the heap if the request exceeds a certain size in bytes given by `_ALLOCA_S_THRESHOLD`. The difference between `_malloca` and `_alloca` is that `_alloca` always allocates on the stack, regardless of the size. Unlike `_alloca`, which does not require or permit a call to `free` to free the memory so allocated, `_malloca` requires the use of [_freea](../VS_visualcpp/_freea.md) to free memory. In debug mode, `_malloca` always allocates memory from the heap.  
  
 There are restrictions to explicitly calling `_malloca` in an exception handler (EH). EH routines that run on x86-class processors operate in their own memory frame: They perform their tasks in memory space that is not based on the current location of the stack pointer of the enclosing function. The most common implementations include Windows NT structured exception handling (SEH) and C++ catch clause expressions. Therefore, explicitly calling `_malloca` in any of the following scenarios results in program failure during the return to the calling EH routine:  
  
-   Windows NT SEH exception filter expression: `__except` (`_malloca ()` )  
  
-   Windows NT SEH final exception handler: `__finally` {`_malloca ()` }  
  
-   C++ EH catch clause expression  
  
 However, `_malloca` can be called directly from within an EH routine or from an application-supplied callback that gets invoked by one of the EH scenarios previously listed.  
  
> [!IMPORTANT]
>  In Windows XP, if `_malloca` is called inside a try/catch block, you must call [_resetstkoflw](../VS_visualcpp/_resetstkoflw.md) in the catch block.  
  
 In addition to the above restrictions, when using the [/clr (Common Language Runtime Compilation)](../VS_visualcpp/-clr--Common-Language-Runtime-Compilation-.md) option, `_malloca` cannot be used in `__except` blocks. For more information, see [/clr Restrictions](../VS_visualcpp/-clr-Restrictions.md).  
  
## Requirements  
  
|Routine|Required header|  
|-------------|---------------------|  
|`_malloca`|<malloc.h>|  
  
## Example  
  
```  
// crt_malloca_simple.c  
#include <stdio.h>  
#include <malloc.h>  
  
void Fn()  
{  
   char * buf = (char *)_malloca( 100 );  
   // do something with buf  
   _freea( buf );  
}  
  
int main()  
{  
   Fn();  
}  
```  
  
## Example  
  
```  
// crt_malloca_exception.c  
// This program demonstrates the use of  
// _malloca and trapping any exceptions  
// that may occur.  
  
#include <windows.h>  
#include <stdio.h>  
#include <malloc.h>  
  
int main()  
{  
    int     size;  
    int     numberRead = 0;  
    int     errcode = 0;  
    void    *p = NULL;  
    void    *pMarker = NULL;  
  
    while (numberRead == 0)  
    {  
        printf_s("Enter the number of bytes to allocate "  
                 "using _malloca: ");  
        numberRead = scanf_s("%d", &size);  
    }  
  
    // Do not use try/catch for _malloca,  
    // use __try/__except, since _malloca throws  
    // Structured Exceptions, not C++ exceptions.  
  
    __try  
    {  
        if (size > 0)  
        {  
            p =  _malloca( size );  
        }  
        else  
        {  
            printf_s("Size must be a positive number.");  
        }  
        _freea( p );  
    }  
  
    // Catch any exceptions that may occur.  
    __except( GetExceptionCode() == STATUS_STACK_OVERFLOW )  
    {  
        printf_s("_malloca failed!\n");  
  
        // If the stack overflows, use this function to restore.  
        errcode = _resetstkoflw();  
        if (errcode)  
        {  
            printf("Could not reset the stack!");  
            _exit(1);  
        }  
    };  
}  
```  
  
## Input  
  
```  
1000  
```  
  
## Sample Output  
  
```  
Enter the number of bytes to allocate using _malloca: 1000  
```  
  
## .NET Framework Equivalent  
 Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## See Also  
 [Memory Allocation](../VS_visualcpp/Memory-Allocation.md)   
 [calloc](../VS_visualcpp/calloc.md)   
 [malloc](../VS_visualcpp/malloc.md)   
 [realloc](../VS_visualcpp/realloc.md)   
 [_resetstkoflw](../VS_visualcpp/_resetstkoflw.md)