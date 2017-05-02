---
title: "IDebugDocumentText::GetPositionOfLine | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetPositionOfLine
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetPositionOfLine"
ms.assetid: d1e6e81b-ddec-4a7c-9b6a-d199e3debfc2
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetPositionOfLine
返回一个字符位置与行的第一个字符相对应。  
  
## 语法  
  
```  
HRESULT GetPositionOfLine(  
   ULONG   cLineNumber,  
   ULONG*  pcCharacterPosition  
);  
```  
  
#### 参数  
 `cLineNumber`  
 \[in\]行号。  
  
 `pcCharacterPosition`  
 \[out\]在行 `cLineNumber`开始时向文档中的字符位置。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法返回字符位置与行的第一个字符相对应。  
  
## 请参阅  
 [IDebugDocumentText 接口](../../winscript/reference/idebugdocumenttext-interface.md)