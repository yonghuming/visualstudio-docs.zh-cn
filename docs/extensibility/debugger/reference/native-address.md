---
title: "NATIVE_ADDRESS | Microsoft Docs"
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
  - "NATIVE_ADDRESS"
helpviewer_keywords: 
  - "NATIVE_ADDRESS 结构"
ms.assetid: 7a0cd085-bfc8-45cc-a3d4-4459070e207a
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# NATIVE_ADDRESS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此结构表示本机地址。  
  
## 语法  
  
```cpp  
typedef struct _tagNATIVE_ADDRESS {  
   DWORD unknown;  
} NATIVE_ADDRESS;  
```  
  
```c#  
public struct NATIVE_ADDRESS {  
   public uint unknown;  
}  
```  
  
## 术语  
 未知  
 native address \(此的含义取决于运行时和操作系统\)。  
  
## 备注  
 此结构是联合的一部分。 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) 结构时， `DEBUG_ADDRESS_UNION` 结构的 `dwKind` 字段设置为 `ADDRESS_KIND_NATIVE` 时 \(从 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) 枚举的值\)。  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)