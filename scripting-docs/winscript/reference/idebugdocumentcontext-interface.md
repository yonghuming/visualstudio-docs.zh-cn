---
title: "IDebugDocumentContext 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentContext 接口"
ms.assetid: 665ee08a-5c6a-4ab1-ab93-de376acc9a74
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugDocumentContext 接口
提供文档的一部分抽象表示正在调试的。  为文本文档，这表示包含字符位置范围。  
  
 除了从 `IUnknown` 继承的方法之外，`IDebugDocumentContext` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IDebugDocumentContext::GetDocument](../../winscript/reference/idebugdocumentcontext-getdocument.md)|返回包含此上下文的文档。|  
|[IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)|枚举代码上下文与此文档上下文。|