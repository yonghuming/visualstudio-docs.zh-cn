---
title: "IDebugCodeContext2 | Microsoft Docs"
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
  - "IDebugCodeContext2"
helpviewer_keywords: 
  - "IDebugCodeContext2 接口"
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCodeContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示代码命令的起始位置。  设置为当天大多数运行时体系结构，代码上下文可视为在程序执行流的地址。  
  
## 语法  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## 实现者说明  
 调试引擎实现此接口与文档位置相关代码命令的位置。  
  
## 调用方的说明  
 在大多数接口的方法，但最常见，返回此接口 [GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)。  它广泛还用于 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) 接口以及在断点解析信息。  
  
## 方法按 Vtable 顺序  
 除了在 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 接口的方法之外，此接口执行以下方法:  
  
|方法|说明|  
|--------|--------|  
|[GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md)|获取对应于活动代码上下文的文档上下文。|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|获取此代码上下文的语言信息。|  
  
## 备注  
 `IDebugCodeContext2` 接口和 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 接口之间的主要差异是 `IDebugCodeContext2` 始终命令对齐。  这意味着 `IDebugCodeContext2` 始终指向命令的开头，，而 `IDebugMemoryContext2` 在运行时结构中可以指向所有字节内存。  `IDebugCodeContext2` 由命令增加而不是基本存储范围 \(通常为字节\)。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [CanSetNextStatement](../Topic/IDebugThread2::CanSetNextStatement.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)   
 [下一步](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)