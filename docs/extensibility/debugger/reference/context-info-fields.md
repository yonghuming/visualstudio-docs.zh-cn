---
title: "CONTEXT_INFO_FIELDS | Microsoft Docs"
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
  - "CONTEXT_INFO_FIELDS"
helpviewer_keywords: 
  - "CONTEXT_INFO_FIELDS 枚举"
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# CONTEXT_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定检索的信息有关内存上下文。  
  
## 语法  
  
```cpp#  
enum enum_CONTEXT_INFO_FIELDS {   
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
typedef DWORD CONTEXT_INFO_FIELDS;  
```  
  
```c#  
public enum enum_CONTEXT_INFO_FIELDS {  
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
```  
  
## 成员  
 CIF\_MODULEURL  
 初始化\/使用 [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md) 结构的 `bstrModuleUrl` 字段。  
  
 CIF\_FUNCTION  
 初始化\/使用 `CONTEXT_INFO` 结构的 `bstrFunction` 字段。  
  
 CIF\_FUNCTIONOFFSET  
 初始化\/使用 `CONTEXT_INFO` 结构的 `posFunctionOffset` 字段。  
  
 CIF\_ADDRESS  
 初始化\/使用 `CONTEXT_INFO` 结构的 `bstrAddress` 字段。  
  
 CIF\_ADDRESSOFFSET  
 初始化\/使用 `CONTEXT_INFO` 结构的 `bstrAddressOffset` 字段。  
  
 CIF\_ALLFIELDS  
 初始化\/使用 `CONTEXT_INFO` 结构的所有字段。  
  
## 备注  
 这些值将参数传递给指示 [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md) 结构的哪些 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) 方法字段进行初始化。  
  
 这些标志也用于指示 `CONTEXT_INFO` 结构的哪些字段是使用和有效，当结构返回时。  
  
 这些值可能按位组合使用或。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)