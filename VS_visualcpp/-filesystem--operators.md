---
title: "&lt;filesystem&gt; operators"
ms.custom: na
ms.date: 10/06/2016
ms.devlang: 
  - C++
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-cpp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 102c4833-aa3b-41a8-8998-f5003c546bfd
caps.latest.revision: 11
manager: ghogen
translation.priority.mt: 
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
# &lt;filesystem&gt; operators
The operators perform a lexical comparison of two paths as strings. Use the **equivalent** function to determine whether two paths (for example a relative path and an absolute path) refer to the same file or directory on disk.  
  
```  
C:\root > D:\root: false  
C:\root > C:\root\sub: false  
C:\root > C:\roo: true  
  
```  
  
 For more information, see [File System Navigation (C++)](../VS_visualcpp/File-System-Navigation.md).  
  
## operator==  
  
```  
bool operator==(const path& left, const path& right) noexcept;  
```  
  
 The function returns left.native() == right.native().  
  
## operator!=  
  
```  
bool operator!=(const path& left, const path& right) noexcept;  
```  
  
 The function returns !(left == right).  
  
## operator<  
  
```  
bool operator<(const path& left, const path& right) noexcept;  
```  
  
 The function returns left.native() < right.native().  
  
## operator<=  
  
```  
bool operator<=(const path& left, const path& right) noexcept;  
```  
  
 The function returns !(right < left).  
  
## operator>  
  
```  
bool operator>(const path& left, const path& right) noexcept;  
```  
  
 The function returns right < left.  
  
## operator>=  
  
```  
bool operator>=(const path& left, const path& right) noexcept;  
```  
  
 The function returns !(left < right).  
  
## operator/  
  
```  
path operator/(const path& left, const path& right);  
```  
  
 The function executes:  
  
```  
basic_string<Elem, Traits> str;  
path ans = left;  
return (ans /= right);  
  
```  
  
## operator<<  
  
```  
template<class Elem, class Traits>    basic_ostream<Elem, Traits>&    operator<<(basic_ostream<Elem, Traits>& os, const path& pval);  
```  
  
 The function returns os << pval.string<Elem, Traits>().  
  
## operator>>  
  
```  
template<class Elem, class Traits>    basic_istream<Elem, Traits>&    operator<<(basic_istream<Elem, Traits>& is, const path& pval);  
```  
  
 The function executes:  
  
```  
basic_string<Elem, Traits> str;  
is >> str;  
pval = str;  
return (is);  
  
```  
  
## See Also  
 [path Class (C++ Standard Template Library)](../VS_visualcpp/path-Class--C---Standard-Template-Library-.md)   
 [File System Navigation (C++)](../VS_visualcpp/File-System-Navigation.md)   
 [<filesystem\>](../VS_visualcpp/-filesystem-.md)