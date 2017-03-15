---
title: "BPREQI_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BPREQI_FIELDS"
helpviewer_keywords: 
  - "BPREQI_FIELDS 枚举"
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# BPREQI_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定要检索的信息有关断点请求。  
  
## 语法  
  
```cpp  
enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
typedef DWORD BPREQI_FIELDS;  
```  
  
```c#  
public enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
```  
  
## 成员  
 BPREQI\_BPLOCATION  
 初始化\/使用 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 或 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 结构的 `bpLocation` \(断点位置\) 字段。  
  
 BPREQI\_LANGUAGE  
 初始化\/使用 `BP_REQUEST_INFO` 或 `BP_REQUEST_INFO2` 结构的 `guidLanguage` 字段。  
  
 BPREQI\_PROGRAM  
 初始化\/使用 `BP_REQUEST_INFO` 或 `BP_REQUEST_INFO2` 结构的 `pProgram` 字段。  
  
 BPREQI\_PROGRAMNAME  
 初始化\/使用 `BP_REQUEST_INFO` 或 `BP_REQUEST_INFO2` 结构的 `bstrProgramName` 字段。  
  
 BPREQI\_THREAD  
 初始化\/使用 `BP_REQUEST_INFO` 或 `BP_REQUEST_INFO2` 结构的 `pThread` 字段。  
  
 BPREQI\_THREADNAME  
 初始化\/使用 `BP_REQUEST_INFO` 或 `BP_REQUEST_INFO2` 结构的 `bstrThreadName` 字段。  
  
 BPREQI\_PASSCOUNT  
 初始化\/使用 `BP_REQUEST_INFO` 或 `BP_REQUEST_INFO2` 结构的 `bpPassCount` 字段。  
  
 BPREQI\_CONDITION  
 初始化\/使用 `BP_REQUEST_INFO` 或 `BP_REQUEST_INFO2` 结构的 `bpCondition` \(断点条件\) 字段。  
  
 BPREQI\_FLAGS  
 初始化\/使用 `BP_REQUEST_INFO` 或 `BP_REQUEST_INFO2` 结构的 `dwFlags` 字段。  
  
 BPREQI\_ALLOLDFIELDS  
 初始化\/使用的所有字段 `BP_REQUEST_INFO` 结构。  
  
 BPREQI\_VENDOR  
 初始化\/使用 `BP_REQUEST_INFO2` 结构的 `guidVendor` 字段。  
  
 BPREQI\_CONSTRAINT  
 初始化\/使用 `BP_REQUEST_INFO2` 结构的 `bstrConstraint` 字段。  
  
 BPREQI\_TRACEPOINT  
 初始化\/使用 `BP_REQUEST_INFO2` 结构的 `bstrTracepoint` 字段。  
  
 BPREQI\_ALLFIELDS  
 为 `BP_REQUEST_INFO2` 结构指定所有字段。  
  
## 备注  
 将作为参数传递 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) 和 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 方法指定 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 和 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 结构的哪些字段进行初始化。  
  
 这些标志也用于指示 `BP_REQUEST_INFO` 和 `BP_REQUEST_INFO2` 结构的哪些字段是使用和有效，在每个结构都返回时。  
  
 这些值可能按位组合使用 `OR`。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)