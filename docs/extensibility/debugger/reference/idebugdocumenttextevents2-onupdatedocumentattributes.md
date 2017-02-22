---
title: "IDebugDocumentTextEvents2::onUpdateDocumentAttributes | Microsoft Docs"
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
  - "IDebugDocumentTextEvents2::OnUpdateDocumentAttributes"
helpviewer_keywords: 
  - "IDebugDocumentTextEvents2::onUpdateDocumentAttributes"
ms.assetid: 31b7d151-9ce2-438e-b405-f8cc46b9f537
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentTextEvents2::onUpdateDocumentAttributes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

通知更新了文档属性的事件接收器。  
  
## 语法  
  
```cpp#  
HRESULT onUpdateDocumentAttributes(   
   TEXT_DOC_ATTR_2 textdocattr  
);  
```  
  
```c#  
int onUpdateDocumentAttributes(   
   enum_TEXT_DOC_ATTR_2 textdocattr  
);  
```  
  
#### 参数  
 `textdocattr`  
 \[in\] 标志的组合从指定文档的更新属性的 [TEXT\_DOC\_ATTR\_2](../../../extensibility/debugger/reference/text-doc-attr-2.md) 枚举的。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [TEXT\_DOC\_ATTR\_2](../../../extensibility/debugger/reference/text-doc-attr-2.md)