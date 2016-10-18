---
title: "texture_view::gather_alpha Method"
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
ms.topic: article
ms.assetid: 9f84e7a1-f50c-4ad7-8d9c-6fad6e338d66
caps.latest.revision: 4
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
# texture_view::gather_alpha Method
Samples the texture at the specified coordinates by using the specified sampling configuration and returns the alpha (w) components of the four sampled texels.  
  
## Syntax  
  
```  
const gather_return_type gather_alpha(  
   const sampler& _Sampler,  
   const coordinates_type& _Coord  
) const restrict(amp);  
  
template<  
   address_mode _Address_mode = address_clamp  
>  
const gather_return_type gather_alpha(  
   const coordinates_type& _Coord  
) const restrict(amp);  
```  
  
#### Parameters  
 `_Address_mode`  
 The address mode to use to sample the `texture_view`. The address mode is the same for all dimensions.  
  
 `_Sampler`  
 The sampler configuration to use to sample the `texture_view`.  
  
 `_Coord`  
 The coordinates to take the sample from. Fractional coordinate values are used to interpolate between sample texels.  
  
## Return Value  
 A rank 4 short vector containing the alpha (w) component of the 4 sampled texel values.  
  
## Requirements  
 **Header:** amp_graphics.h  
  
 **Namespace:** concurrency::graphics  
  
## See Also  
 [texture_view Class](../VS_visualcpp/texture_view-Class.md)