---
title: "UNMANAGED_ADDRESS_PHYSICAL | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UNMANAGED_ADDRESS_PHYSICAL"
helpviewer_keywords: 
  - "UNMANAGED_ADDRESS_PHYSICAL 结构"
ms.assetid: fed09686-caa6-4efc-851e-a0432019e9d0
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# UNMANAGED_ADDRESS_PHYSICAL
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此结构表示一个物理地址。  
  
## 语法  
  
```cpp  
typedef struct _tagUNMANAGED_ADDRESS_PHYSICAL {  
   ULONGLONG offset;  
} UNMANAGED_ADDRESS_PHYSICAL;  
```  
  
```c#  
public struct UNMANAGED_ADDRESS_PHYSICAL {  
   public ulong offset;  
}  
```  
  
## 术语  
 偏移量  
 一个 64 位偏移量一个物理地址空间中。  
  
## 备注  
 此结构是联合的一部分。 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) 结构时， `DEBUG_ADDRESS_UNION` 结构的 `dwKind` 字段设置为 `ADDRESS_KIND_UNMANAGED_PHYSICAL` 时 \(从 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) 枚举的值\)。  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)