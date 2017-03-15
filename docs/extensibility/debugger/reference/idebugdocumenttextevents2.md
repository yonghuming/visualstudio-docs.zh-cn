---
title: "IDebugDocumentTextEvents2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentTextEvents2"
helpviewer_keywords: 
  - "IDebugDocumentTextEvents2 接口"
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugDocumentTextEvents2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口用于通知调试引擎提供的更改的 Visual Studio 对源文档。  
  
## 语法  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## 实现者说明  
 DE implements 支持进行的此接口来更改源代码。  此接口在同一对象通常是实现 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 接口。  
  
## 调用方的说明  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 通过调用获取此接口来 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> 方法。  <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> 接口通过调用获取到 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> 方法。  <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> 接口通过调用 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 接口的 [QueryInterface](/visual-cpp/atl/queryinterface) 方法获取。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugDocumentTextEvents2`方法。  
  
|方法|说明|  
|--------|--------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|指示整个文档销毁了。|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|通知调试包文本插入到文档中。|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|通知调试包文本从文档中移除。|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|通知调试包文本文档中替换。|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|通知调试包文本属性在文档中更新为止。|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|通知更新了文档属性的事件接收器。|  
  
## 备注  
 只调试提供这些文档将利用 `IDebugDocumentTextEvent2` 接口的引擎。  此示例有脚本调试引擎。  在解释脚本过程中，不存在任何磁盘文件并仅了解对 DE 的新源代码中生成。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)