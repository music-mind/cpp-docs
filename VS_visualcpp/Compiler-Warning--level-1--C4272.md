---
title: "Compiler Warning (level 1) C4272"
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
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
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
# Compiler Warning (level 1) C4272
'function' : is marked __declspec(dllimport); must specify native calling convention when importing a function.  
  
 It is an error to export a function marked with the [__clrcall](../VS_visualcpp/__clrcall.md) calling convention, and the compiler issues this warning if you attempt to import a function marked `__clrcall`.  
  
 The following sample generates C4272:  
  
```  
// C4272.cpp  
// compile with: /c /W1 /clr  
__declspec(dllimport) void __clrcall Test();   // C4272  
__declspec(dllimport) void Test2();   // OK  
```