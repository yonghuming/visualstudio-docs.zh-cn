---
title: "IDebugDocumentTextAuthor::ReplaceText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextAuthor.ReplaceText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentTextAuthor::ReplaceText"
ms.assetid: f89304e6-5be0-45a5-947d-2c59c3c0a05e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextAuthor::ReplaceText
替换文档中的文本。  
  
## 语法  
  
```  
HRESULT ReplaceText(  
   ULONG    cCharacterPosition,  
   ULONG    cNumToReplace,  
   OLECHAR  pcharText[]  
);  
```  
  
#### 参数  
 `cCharacterPosition`  
 \[in\]启动字符范围的位置替换。  
  
 `cNumToReplace`  
 \[in\]要替换的字符数。  
  
 `pcharText[]`  
 \[in\]包含新字符的缓冲区替换字符。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法替换文档中的文本。  
  
## 请参阅  
 [IDebugDocumentTextAuthor 接口](../../winscript/reference/idebugdocumenttextauthor-interface.md)