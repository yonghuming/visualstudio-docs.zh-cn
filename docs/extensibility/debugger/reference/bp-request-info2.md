---
title: "BP_REQUEST_INFO2 | Microsoft Docs"
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
  - "BP_REQUEST_INFO2"
helpviewer_keywords: 
  - "BP_REQUEST_INFO2 结构"
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_REQUEST_INFO2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

包含要求的信息实现断点，包括供应商 GUID、约束和跟踪点。  
  
## 语法  
  
```cpp#  
typedef struct _BP_REQUEST_INFO2 {  
   BPREQI_FIELDS   dwFields;  
   GUID            guidLanguage;  
   BP_LOCATION     bpLocation;  
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   IDebugThread2*  pThread;  
   BSTR            bstrThreadName;  
   BP_CONDITION    bpCondition;  
   BP_PASSCOUNT    bpPassCount;  
   BP_FLAGS        dwFlags;  
   GUID            guidVendor;  
   BSTR            bstrConstraint;  
   BSTR            bstrTracepoint;  
} BP_REQUEST_INFO2;  
```  
  
```c#  
public struct BP_REQUEST_INFO2 {  
   public uint           dwFields;  
   public Guid           guidLanguage;  
   public BP_LOCATION    bpLocation;  
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public IDebugThread2  pThread;  
   public string         bstrThreadName;  
   public BP_CONDITION   bpCondition;  
   public BP_PASSCOUNT   bpPassCount;  
   public uint           dwFlags;  
   public Guid           guidVendor;  
   public string         bstrConstraint;  
   public string         bstrTracepoint;  
};  
```  
  
## 成员  
 `dwFields`  
 标志的组合从指定的 [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) 枚举的哪些字段。完成。  
  
 `guidLanguage`  
 语言 GUID。  
  
 `bpLocation`  
 指定断点位置的类型的 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 结构。  
  
 `pProgram`  
 表示应用程序断点发生的 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 对象。  
  
 `bstrProgramName`  
 断点发生应用程序的名称。  
  
 `pThread`  
 表示线程断点发生的 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 对象。  
  
 `bstrThreadName`  
 断点线程上出现的名称。  
  
 `bpCondition`  
 描述条件断点将激发的 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) 结构。  
  
 `bpPassCount`  
 包含断点的通过计数信息的 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) 结构。  
  
 `dwFlags`  
 标志的组合。为请求的断点指定标志的 [BP\_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) 枚举的。  
  
 `guidVendor`  
 供应商 GUID。  可能为 null 值。  
  
 `bstrConstraint`  
 断点约束的名称。  可能为 null 值。  
  
 `bstrTracepoint`  
 跟踪的名称点。  可能为 null 值。  
  
## 备注  
 此 framework 使用 [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md) 方法返回。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)   
 [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)