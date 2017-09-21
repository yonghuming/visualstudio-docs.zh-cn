---
title: "MACHINE_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MACHINE_INFO"
helpviewer_keywords: 
  - "MACHINE_INFO 结构"
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# MACHINE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

描述特定计算机。  
  
## 语法  
  
```cpp#  
typedef struct tagMACHINE_INFO {   
   MACHINE_INFO_FIELDS Fields;  
   BSTR                bstrName;  
   MACHINE_INFO_FLAGS  Flags;  
} MACHINE_INFO;  
```  
  
```c#  
public struct MACHINE_INFO {   
   public uint   Fields;  
   public string bstrName;  
   public uint   Flags;  
};  
```  
  
## 成员  
 `Fields`  
 指定标志的组合。 [MACHINE\_INFO\_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) 枚举结构的哪些字段初始化。  
  
 `bstrName`  
 计算机名称。  调用 [GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)等效。  
  
 `Flags`  
 标志的组合。描述设备特性的 [MACHINE\_INFO\_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) 枚举的。  
  
## 备注  
 此结构通过对 [GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md) 方法的调用返回。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MACHINE\_INFO\_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)   
 [GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md)