---
title: "PDB_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PDB_TYPE"
helpviewer_keywords: 
  - "PDB_TYPE 结构"
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# PDB_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此结构指定有关从 PDB 符号执行的字段类型的信息。  
  
## 语法  
  
```cpp#  
typedef struct _tagTYPE_PDB {  
   ULONG32 ulAppDomainID;  
   GUID    guidModule;  
   DWORD   symid;  
} PDB_TYPE;  
```  
  
```c#  
public struct PDB_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public uint symid;  
};  
```  
  
#### 参数  
 ulAppDomainID  
 符号来自应用程序的 ID。  用于唯一标识应用程序的实例。  
  
 guidModule  
 包含此域模块的 GUID。  
  
 symid  
 对应于此字段符号的 ID。  
  
## 备注  
 此结构显示为 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) 结构的联合一部分，当 `TYPE_INFO` 结构的 `dwKind` 字段设置为 `TYPE_KIND_PDB` 时 \(从 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) 枚举的值\)。  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)