---
title: "entry (C++ COM Attribute) | Microsoft Docs"
ms.custom: ""
ms.date: "10/02/2018"
ms.technology: ["cpp-windows"]
ms.topic: "reference"
f1_keywords: ["vc-attr.entry"]
dev_langs: ["C++"]
helpviewer_keywords: ["entry attribute"]
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
author: "mikeblome"
ms.author: "mblome"
ms.workload: ["cplusplus", "uwp"]
---
# entry

Specifies an exported function or constant in a module by identifying the entry point in the DLL.

## Syntax

```cpp
[ entry(id) ]
```

### Parameters

*id*<br/>
The ID of the entry point.

## Remarks

The **entry** C++ attribute has the same functionality as the [entry](/windows/desktop/Midl/entry) MIDL attribute.

## Example

See the example for [idl_module](idl-module.md) for an example use of **entry**.

## Requirements

### Attribute Context

|||
|-|-|
|**Applies to**|`idl_module` attribute|
|**Repeatable**|No|
|**Required attributes**|None|
|**Invalid attributes**|None|

For more information, see [Attribute Contexts](cpp-attributes-com-net.md#contexts).

## See Also

[IDL Attributes](idl-attributes.md)