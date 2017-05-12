---
title: "IDebugDocumentText 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentText 接口"
ms.assetid: 242bad79-9c0a-4a30-879a-9f43db4e022b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText 接口
提供对调试的只会写入版本文档。  此接口使用以下约定：  
  
-   字符位置和行号是基于零。  
  
-   字符位置表示字符偏移量;它们不表示字节或字偏移量。  对于Win32中，字符位置是Unicode偏移量。  
  
 除了从 `IDebugDocument` 继承的方法之外，`IDebugDocumentText` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IDebugDocumentText::GetDocumentAttributes](../../winscript/reference/idebugdocumenttext-getdocumentattributes.md)|返回文档的属性。|  
|[IDebugDocumentText::GetSize](../../winscript/reference/idebugdocumenttext-getsize.md)|返回行的字符数和数字文档中的。|  
|[IDebugDocumentText::GetPositionOfLine](../../winscript/reference/idebugdocumenttext-getpositionofline.md)|返回字符位置与行的第一个字符相对应。|  
|[IDebugDocumentText::GetLineOfPosition](../../winscript/reference/idebugdocumenttext-getlineofposition.md)|返回行号，因此，可选择，字符按对应于特定字符位置的行中。|  
|[IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)|检索字符和字符的属性与字符位置范围。|  
|[IDebugDocumentText::GetPositionOfContext](../../winscript/reference/idebugdocumenttext-getpositionofcontext.md)|返回字符位置大小与文档上下文相对应。|  
|[IDebugDocumentText::GetContextOfPosition](../../winscript/reference/idebugdocumenttext-getcontextofposition.md)|创建一个文档上下文对象与提供的字符位置范围相对应。|