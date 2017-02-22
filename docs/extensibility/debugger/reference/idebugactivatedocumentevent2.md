---
title: "IDebugActivateDocumentEvent2 | Microsoft Docs"
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
  - "IDebugActivateDocumentEvent2"
helpviewer_keywords: 
  - "IDebugActivateDocumentEvent2 接口"
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugActivateDocumentEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

调试引擎 \(DE\)使用此接口请求加载文档。  
  
## 语法  
  
```  
IDebugActivateDocumentEvent2 : IUnknown  
```  
  
## 实现者说明  
 DE implements 此接口，并根据需要源文件以打开它。  此接口只实现由调试工作与的引擎或这些脚本解释器的部件。  在对象必须实现 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 接口和此接口相同 \(SDM 使用 [QueryInterface](/visual-cpp/atl/queryinterface) 访问 `IDebugEvent2` 接口\)。  
  
## 调用方的说明  
 ，它需要具有源文件中打开时，、创建和发送此事件对象。  ，它附加到正在调试的程序，该事件发送通过使用 SDM 提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回调函数。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugActivateDocumentEvent2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetDocument](../Topic/IDebugActivateDocumentEvent2::GetDocument.md)|获取活动文档。|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|获取描述在文档中的位置的文档上下文。|  
  
## 备注  
 此接口使用的典型方案是，如果分析错误在 HTML 页的脚本代码生成，该脚本、发送此接口添加到 SDM，以便与分析错误的文档中显示。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)