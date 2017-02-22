---
title: "调用堆栈评估 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试 [调试 SDK]，调用堆栈评估"
  - "调用堆栈、 评估"
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# 调用堆栈评估
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在中断模式下，才能查看调用堆栈的堆栈帧，必须执行 [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 方法。  
  
## 计算的方法  
 对于简单只调试引擎 \(DE\)，可能存在一个堆栈帧。  在中断模式下，若要检查堆栈帧，必须执行 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)以下方法。  
  
|方法|说明|  
|--------|--------|  
|[GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)|获取堆栈帧的代码上下文。  代码上下文表示堆栈帧的当前指令指针。|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|获取堆栈帧的文档上下文。  文档上下文表示源代码中的当前位置堆栈帧的。  对查看源代码，当您在程序终止。|  
  
 这些方法需要几个上下文相关的接口和方法的实现。  因此，必须执行 [GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md) 方法和 [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md)以下方法。  
  
|方法|说明|  
|--------|--------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|获取文档上下文的文件语句之间。|  
  
 若要枚举代码上下文，必须执行 [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)所有方法。  
  
## 请参阅  
 [执行控制和状态评估](../../extensibility/debugger/execution-control-and-state-evaluation.md)