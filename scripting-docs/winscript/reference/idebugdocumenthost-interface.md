---
title: "IDebugDocumentHost 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentHost 接口"
ms.assetid: 2fed4220-b6a2-47c6-bf28-daad7dd5c42d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost 接口
公开宿主特定功能，比如语法着色，在调试器。  `IDebugDocumentHelper::SetDebugDocumentHost` 方法采用此接口作为参数。  
  
 除了从 `IUnknown` 继承的方法之外，`IDebugDocumentHost` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|使用 `IDebugDocumentHelper::AddDeferredText`，返回添加字符的范围，原始宿主文档。|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|返回块的文本属性文档文本。|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|通知宿主新文档上下文创建，并允许宿主选择性地返回对象控制新的上下文。|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|返回完整路径\(包括文件名\)文档源文件。|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|返回文档的名称，而无需路径信息。|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|通知宿主文档源文件中保存了，并且应刷新其内容。|