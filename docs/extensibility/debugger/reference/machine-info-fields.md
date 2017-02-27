---
title: "MACHINE_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MACHINE_INFO_FIELDS"
helpviewer_keywords: 
  - "MACHINE_INFO_FIELDS 枚举"
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# MACHINE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定检索哪种信息为特定设备。  
  
## 语法  
  
```cpp#  
enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
typedef DWORD MACHINE_INFO_FIELDS;  
```  
  
```c#  
public enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
```  
  
## 成员  
 MCIF\_NAME  
 初始化\/使用结构中的 `bstrName` 字段。  
  
 MCIF\_FLAGS  
 初始化\/使用结构中的 `Flags` 字段。  
  
 MIF\_ALL  
 对结构的字段的初始化\/使用所有。  
  
## 备注  
 这些值传递给 [GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md) 方法指示 [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md) 结构的哪些成员进行初始化。  
  
 还用于在 `MACHINE_INFO` 结构的 `Fields` 成员指示哪些字段是使用和有效。  
  
 这些标志可以按位组合使用 `OR`。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md)   
 [GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md)