---
title: "THREADPROPERTIES | Microsoft Docs"
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
  - "THREADPROPERTIES"
helpviewer_keywords: 
  - "THREADPROPERTIES 结构"
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# THREADPROPERTIES
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

描述线程的属性。  
  
## 语法  
  
```cpp#  
typedef struct _tagTHREADPROPERTIES {   
   THREADPROPERTY_FIELDS dwFields;  
   DWORD                 dwThreadId;  
   DWORD                 dwSuspendCount;  
   DWORD                 dwThreadState;  
   BSTR                  bstrPriority;  
   BSTR                  bstrName;  
   BSTR                  bstrLocation;  
} THREADPROPERTIES;  
```  
  
```c#  
public struct THREADPROPERTIES {   
   public uint   dwFields;  
   public uint   dwThreadId;  
   public uint   dwSuspendCount;  
   public uint   dwThreadState;  
   public string bstrPriority;  
   public string bstrName;  
   public string bstrLocation;  
};  
```  
  
## 成员  
 dwFields  
 标志的组合。 [THREADPROPERTY\_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) 枚举的，描述此结构中的哪些字段有效。  
  
 dwThreadId  
 线程 ID.  
  
 dwSuspendCount  
 线程挂起计数。  
  
 dwThreadState  
 从指示运行线程状态的 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) 枚举的值。  
  
 bstrPriority  
 指定线程优先级的字符串;例如， “常规”， “essential 常规”或 “的时间上”。  
  
 bstName  
 线程名称。  
  
 bstrLocation  
 \(通常最顶层的堆栈帧\)，通常是以执行当前暂停方法的名称线程位置。  
  
## 备注  
 此结构通过对 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) 方法的调用填充。  因此返回的信息通常用于填充 **线程** 窗口。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY\_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)