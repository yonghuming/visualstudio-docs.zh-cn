---
title: "IDebugDocumentTextExternalAuthor 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentTextExternalAuthor 接口"
ms.assetid: 0b04de1b-f922-4526-af4e-c0af2b7c1ce4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextExternalAuthor 接口
允许外部编辑器安全编辑基于文件的调试器通过通知文档，更改时源文件。  
  
 除了从 `IUnknown` 继承的方法之外，`IDebugDocumentTextExternalAuthor` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IDebugDocumentTextExternalAuthor::GetPathName](../../winscript/reference/idebugdocumenttextexternalauthor-getpathname.md)|返回文档的完整路径和文件名。|  
|[IDebugDocumentTextExternalAuthor::GetFileName](../../winscript/reference/idebugdocumenttextexternalauthor-getfilename.md)|返回文档的名称，而不用路径信息。|  
|[IDebugDocumentTextExternalAuthor::NotifyChanged](../../winscript/reference/idebugdocumenttextexternalauthor-notifychanged.md)|通知宿主文档源已更改。|