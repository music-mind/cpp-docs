---
title: "&#39;Line&#39; statements are no longer supported (Smart Device-Visual Basic Compiler Error)"
ms.custom: na
ms.date: "10/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: na
ms.topic: "article"
f1_keywords: 
  - "vbc30768"
  - "bc30768"
helpviewer_keywords: 
  - "BC30768"
ms.assetid: e7a17c77-06bb-4d33-966e-addb4f51caaf
caps.latest.revision: 8
ms.author: "billchi"
manager: "douge"
translation.priority.ht: 
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "ru-ru"
  - "zh-cn"
  - "zh-tw"
translation.priority.mt: 
  - "cs-cz"
  - "pl-pl"
  - "pt-br"
  - "tr-tr"
---
# &#39;Line&#39; statements are no longer supported (Smart Device/Visual Basic Compiler Error)
The `Line` statement is no longer supported. File I/O functionality is normally available as \<xref:Microsoft.VisualBasic.FileSystem.LineInput*?displayProperty=fullName>, but the targeted version of the .NET Compact Framework does not support it.  
  
 **Error ID:** BC30768  
  
### To correct this error  
  
-   If performing file access, use the functions defined in the \<xref:System.IO> namespace.  
  
-   If performing graphics, use \<xref:System.Drawing.Graphics.DrawLine*?displayProperty=fullName>.  
  
## See Also  
 \<xref:System.IO>   
 \<xref:System.Drawing>   
 [File Access with Visual Basic](../Topic/File%20Access%20with%20Visual%20Basic.md)