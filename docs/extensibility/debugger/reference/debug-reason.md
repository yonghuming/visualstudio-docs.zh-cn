---
title: "DEBUG_REASON | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_REASON"
helpviewer_keywords: 
  - "DEBUG_REASON 枚举"
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# DEBUG_REASON
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定进程的原因。调试生成。  
  
## 语法  
  
```cpp#  
enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
typedef DWORD DEBUG_REASON;  
```  
  
```c#  
public enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
```  
  
#### 参数  
 DEBUG\_REASON\_ERROR  
 一个未指定的发生错误 \(这用作默认条件，当相应的非其他原因时\)。  
  
 DEBUG\_REASON\_USER\_LAUNCHED  
 处理生成了基于用户请求。  
  
 DEBUG\_REASON\_USER\_ATTACHED  
 正在运行的进程附加到由用户。  
  
 DEBUG\_REASON\_AUTO\_ATTACHED  
 ，在其生成时，转换过程将自动附加到。  
  
 DEBUG\_REASON\_CAUSALITY  
 处理生成的是由于一个实时 \(JIT\)调试事件。  
  
## 备注  
 返回从 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) 方法。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)