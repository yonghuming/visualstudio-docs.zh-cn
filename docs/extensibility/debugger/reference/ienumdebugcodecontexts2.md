---
title: "IEnumDebugCodeContexts2 | Microsoft Docs"
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
  - "IEnumDebugCodeContexts2"
helpviewer_keywords: 
  - "IEnumDebugCodeContexts2"
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugCodeContexts2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口枚举代码上下文与调试会话，或者与特定程序或文档。  
  
## 语法  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎 \(DE\)实现此接口表示代码上下文列出特定文本位置的过程中，或代码上下文列出特定的文档上下文。  
  
## 调用方的说明  
 调用 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) 获取表示代码上下文中列出给定文本位置的该接口在程序的源文档。  
  
 调用 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) 获取表示任何代码上下文的列表特定的此接口源文档。  
  
## 方法按 Vtable 顺序  
 下表显示 `IEnumDebugCodeContexts2`方法。  
  
|方法|说明|  
|--------|--------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|检索代码上下文指定数目的枚举序列的。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|跳过代码上下文指定数目的枚举序列的。|  
|[重置](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|重置枚举序列与开头。|  
|[克隆](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|创建包含枚举状态和枚举当前枚举数相同的枚举数。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|获取代码上下文数枚举数。|  
  
## 备注  
 Visual Studio 会调用 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) 填充的代码上下文列出用户可以选择自，当设置下一语句或显示源文件时反汇编。  ，当具有 c. c\+\+ 样式模板时，多个实例，如多个代码上下文会发生此错误。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)