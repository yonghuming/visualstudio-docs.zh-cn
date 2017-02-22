---
title: "IDebugDocumentText2 | Microsoft Docs"
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
  - "IDebugDocumentText2"
helpviewer_keywords: 
  - "IDebugDocumentText2 接口"
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentText2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示文本文档。  
  
## 语法  
  
```  
IDebugDocumentText2 : IDebugDocument2  
```  
  
## 实现者说明  
 它需要提供时的调试引擎 \(DE\)实现此接口，当源代码以文本形式。  因为这是最典型的情况，因此，如果 DE implements [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 接口，它还应当实现 `IDebugDocumentText2` 接口。  
  
## 调用方的说明  
 使用 `QueryInterface` 方法从 `IDebugDocument2` 接口的此接口。  
  
## 方法按 Vtable 顺序  
 除了在 `IDebugDocument2` 接口的方法之外，此接口执行以下方法:  
  
|方法|说明|  
|--------|--------|  
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|检索文本的范围在文档中的该位置。|  
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|文档中的指定位置检索文本。|  
  
## 备注  
 对象实现此接口还必须实现 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> 接口，提供 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) 对象的 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> 接口。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)