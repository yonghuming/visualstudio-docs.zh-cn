---
title: "IDebugDocumentText::GetDocumentAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetDocumentAttributes
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetDocumentAttributes"
ms.assetid: 8c544ca1-8db4-4bca-973e-09315d9a0ee5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetDocumentAttributes
返回文档的属性。  
  
## 语法  
  
```  
HRESULT GetDocumentAttributes(  
   TEXT_DOC_ATTR*  ptextdocattr  
);  
```  
  
#### 参数  
 `ptextdocattr`  
 \[in\]文档中的文本属性。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法返回文档的属性。  
  
## 请参阅  
 [IDebugDocumentText 接口](../../winscript/reference/idebugdocumenttext-interface.md)   
 [TEXT\_DOC\_ATTR 常量](../../winscript/reference/text-doc-attr-constants.md)