---
title: "IDebugDocumentPositionOffset2 | Microsoft Docs"
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
  - "IDebugDocumentPositionOffset2 接口"
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentPositionOffset2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

表示源文件中的位置作为字符偏移量。  
  
## 语法  
  
```  
IDebugDocumentPositionOffset2 : IUnknown  
```  
  
## 实现者说明  
 实现由 IDE 和使用调试引擎。  
  
## 方法  
 下表显示 `IDebugDocumentPositionOffset2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetRange](../Topic/IDebugDocumentPositionOffset2::GetRange.md)|检索的大小当前文件位置。|  
  
## 备注  
 这将返回信息和 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) 相同，但在 `char` 偏移量最初文档。  它显示文档，如它在磁盘，也就是说，一维数组上存在字符，而不是通常返回的行和列信息。  
  
## 要求  
 标题:Msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)