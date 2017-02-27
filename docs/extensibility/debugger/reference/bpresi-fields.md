---
title: "BPRESI_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BPRESI_FIELDS"
helpviewer_keywords: 
  - "BPRESI_FIELDS 枚举"
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# BPRESI_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定要检索的信息有关断点的成功解决。  
  
## 语法  
  
```cpp#  
enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
typedef DWORD BPRESI_FIELDS;  
```  
  
```c#  
public enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
```  
  
## 成员  
 BPRESI\_BPRESLOCATION  
 初始化\/使用 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) 结构的 `bpResLocation` \(断点解析位置\) 字段。  
  
 BPRESI\_PROGRAM  
 初始化\/使用 `BP_RESOLUTION_INFO` 结构的 `pProgram` 字段。  
  
 BPRESI\_THREAD  
 初始化\/使用 `BP_RESOLUTION_INFO` 结构的 `pThread` 字段。  
  
 BPRESI\_ALLFIELDS  
 指定所有字段。  
  
## 备注  
 传递给 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) 方法指示 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) 结构的哪些字段进行初始化。  
  
 这些标志也用于指示 `BP_RESOLUTION_INFO` 结构的哪些字段是使用和有效，当该结构返回时。  
  
 这些值可能按位组合使用 `OR`。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)