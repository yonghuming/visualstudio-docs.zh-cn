---
title: "IDebugDocumentContext2 | Microsoft Docs"
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
  - "IDebugDocumentContext2"
helpviewer_keywords: 
  - "IDebugDocumentContext2"
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示源文件中的位置文档。  
  
## 语法  
  
```  
IDebugDocumentContext2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎 \(DE\)实现此接口作为其一部分的源代码级别调试支持。  除了在源代码中的位置之外，该接口提供比较的上下文方法，并定位通过源代码文档。  
  
## 调用方的说明  
 在一些接口，但最常见 [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) 和 [GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md) 接口的方法，返回此接口。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugDocumentContext2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetDocument](../Topic/IDebugDocumentContext2::GetDocument.md)|获取包含此文档上下文的文档。|  
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|获取包含此文档上下文文档的可显示的名称。|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|检索所有代码上下文列表与此文档上下文。|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|获取该语言与此文档上下文。|  
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|获取此的文件语句之间文档上下文。|  
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|获取此的文件源范围文档上下文。|  
|[比较](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|比较此文档上下文到特定数组文档上下文。|  
|[查找](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|由语句或行的许多移动文档上下文。|  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)   
 [GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md)