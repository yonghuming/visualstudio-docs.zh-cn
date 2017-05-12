---
title: "IDebugDocumentTextAuthor::RemoveText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextAuthor.RemoveText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentTextAuthor::RemoveText"
ms.assetid: 2b74d850-c0b1-4a3c-a37c-2c8d06d1ae02
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextAuthor::RemoveText
从文档中移除文本。  
  
## 语法  
  
```  
HRESULT RemoveText(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToRemove  
);  
```  
  
#### 参数  
 `cCharacterPosition`  
 \[in\]启动字符范围的位置移除。  
  
 `cNumToRemove`  
 \[in\]要移除的字符数。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法从文档中移除文本。  
  
## 请参阅  
 [IDebugDocumentTextAuthor 接口](../../winscript/reference/idebugdocumenttextauthor-interface.md)   
 [IDebugDocumentTextAuthor::InsertText](../../winscript/reference/idebugdocumenttextauthor-inserttext.md)