---
title: "IDebugDocument2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocument2"
helpviewer_keywords: 
  - "IDebugDocument2 接口"
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugDocument2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示源文档。  
  
## 语法  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## 实现者说明  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 通常实现此接口。  调试引擎 \(DE\)还可以实现此接口，则需要提供源代码，并且源磁盘上不存在。  在这种情况下， DE 还将实现 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 和 [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) 接口，以及一些其他方法在 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) 和 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) 接口。  
  
## 调用方的说明  
 在 `IDebugDocumentContext2`、 `IDebugDisassemblyStream2`、 `IDebugDocumentPosition2`和 `IDebugActivateDocumentEvent2` 接口的方法返回此接口。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugDocument2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|在多种形式之一获取文档的名称。|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|获取文档的类标识符。|  
  
## 备注  
 ，仅当 DE 提供源代码时，此接口实现。  例如，进行调试时，在 HTML 页的脚本， DE 提供源代码，因为该源动态下载或生成并不存在作为磁盘文件。  在调试传统语言，如 C\+\+ 时，此接口不需要实现。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../Topic/IDebugActivateDocumentEvent2::GetDocument.md)   
 [GetDocument](../Topic/IDebugDocumentContext2::GetDocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)