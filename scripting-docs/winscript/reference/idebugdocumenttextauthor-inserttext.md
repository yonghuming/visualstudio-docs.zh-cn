---
title: "IDebugDocumentTextAuthor::InsertText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextAuthor.InsertText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentTextAuthor::InsertText"
ms.assetid: ef4e6a5b-8efa-4290-b498-c0f8a6aac09b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextAuthor::InsertText
插入文本到文档中。  
  
## 语法  
  
```  
HRESULT InsertText(  
   ULONG    cCharacterPosition,  
   ULONG    cNumToInsert,  
   OLECHAR  pcharText[]  
);  
```  
  
#### 参数  
 `cCharacterPosition`  
 \[in\]插入文本的位置。  
  
 `cNumToInsert`  
 \[in\]中的字符数要插入的。  
  
 `pcharText[]`  
 \[in\]包含字符的缓冲区插入。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法插入新文本添加到文档中。  
  
## 请参阅  
 [IDebugDocumentTextAuthor 接口](../../winscript/reference/idebugdocumenttextauthor-interface.md)   
 [IDebugDocumentTextAuthor::RemoveText](../../winscript/reference/idebugdocumenttextauthor-removetext.md)