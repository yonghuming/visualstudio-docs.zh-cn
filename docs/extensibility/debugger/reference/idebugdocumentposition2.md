---
title: "IDebugDocumentPosition2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentPosition2"
helpviewer_keywords: 
  - "IDebugDocumentPosition2 接口"
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugDocumentPosition2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示源文件中的抽象位置。  
  
## 语法  
  
```  
IDebugDocumentPosition2 : IUnknown  
```  
  
## 实现者说明  
 Visual Studio 通常实现此接口。  调试引擎 \(DE\)还将实现此接口，则必须提供自己的源代码 \(，当 DE implements [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 接口\)。  
  
## 调用方的说明  
 此接口将作为参数传递 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)。  它也会提供作为又作为 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) framework 的一部分，用于创建挂起的断点的 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 联合 \(特别是， [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) 结构\) 的一部分。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugDocumentPosition2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|获取包含此文档位置源文件的文件名。|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|获取包含文档。|  
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|确定此位置是否位于给定的包含文档。|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|获取此范围文档位置。|  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)