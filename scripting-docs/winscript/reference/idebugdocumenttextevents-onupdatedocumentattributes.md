---
title: "IDebugDocumentTextEvents::onUpdateDocumentAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextEvents.onUpdateDocumentAttributes
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentTextEvents::onUpdateDocumentAttributes"
ms.assetid: 48fa909c-14c2-4ca4-af86-a5809c72dd39
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextEvents::onUpdateDocumentAttributes
指示文档属性已更改。  
  
## 语法  
  
```  
HRESULT onUpdateDocumentAttributes(  
   TEXT_DOC_ATTR  textdocattr  
);  
```  
  
#### 参数  
 `textdocattr`  
 \[in\]新文档属性。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法指示文档属性已更改。  
  
## 请参阅  
 [IDebugDocumentTextEvents 接口](../../winscript/reference/idebugdocumenttextevents-interface.md)   
 [TEXT\_DOC\_ATTR 常量](../../winscript/reference/text-doc-attr-constants.md)