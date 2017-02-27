---
title: "METADATA_ADDRESS_METHOD | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "METADATA_ADDRESS_METHOD"
helpviewer_keywords: 
  - "METADATA_ADDRESS_METHOD 结构"
ms.assetid: fc0e5370-1b4f-4867-837f-0d63c4b9dd09
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# METADATA_ADDRESS_METHOD
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此结构表示类的方法的地址。  
  
## 语法  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_METHOD {  
   _mdToken tokMethod;  
   DWORD    dwOffset;  
   DWORD    dwVersion;  
} METADATA_ADDRESS_METHOD;  
```  
  
```c#  
public struct METADATA_ADDRESS_METHOD {  
   public int  tokMethod;  
   public uint dwOffset;  
   public uint dwVersion;  
}  
```  
  
## 术语  
 tokMethod  
 方法的 ID。  
  
 \[c\+\+\] `_mdToken` 是 32 位 `int`的 `typedef` 。  
  
 dwOffset  
 偏移量从类开始。此方法 \(可以表示偏移量 vtable 中\)。  
  
 dwVersion  
 方法的版本 \(此值设置为符号提供程序是唯一的。\)  
  
## 备注  
 此结构是联合的一部分。 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) 结构时， `DEBUG_ADDRESS_UNION` 结构的 `dwKind` 字段设置为 `ADDRESS_KIND_METHOD` 时 \(从 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) 枚举的值\)。  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)