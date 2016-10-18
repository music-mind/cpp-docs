---
title: "Command-Line Error D8045"
ms.custom: na
ms.date: 10/03/2016
ms.devlang: 
  - C++
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-cpp
ms.tgt_pltfrm: na
ms.topic: error-reference
ms.assetid: 01c8808c-bac1-4b4d-8a90-b595f95e9318
caps.latest.revision: 9
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
# Command-Line Error D8045
cannot compile C file 'file' with the /clr option  
  
 Only C++ source code files can be passed to a compilation that uses **/clr**.  Use **/TP** to compile a .c file as a .cpp file; see [/Tc, /Tp, /TC, /TP (Specify Source File Type)](../VS_visualcpp/-Tc---Tp---TC---TP--Specify-Source-File-Type-.md) for more information.  
  
 For more information, see [/clr (Common Language Runtime Compilation)](../VS_visualcpp/-clr--Common-Language-Runtime-Compilation-.md).  
  
 D8045 can also occur if you compile an ATL application using Visual C++. See [How to: Migrate to /clr](../VS_visualcpp/How-to--Migrate-to--clr.md) for more information.