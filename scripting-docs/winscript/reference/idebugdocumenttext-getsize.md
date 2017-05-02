---
title: "IDebugDocumentText::GetSize | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetSize
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetSize"
ms.assetid: 9da53856-613a-44b2-a84c-99454a2a1548
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetSize
返回行的字符数和数字文档中的。  
  
## 语法  
  
```  
HRESULT GetSize(  
   ULONG*  pcNumLines,  
   ULONG*  pcNumChars  
);  
```  
  
#### 参数  
 `pcNumLines`  
 \[in\]行的编号在文档中。  如果此参数是NULL，方法不返回值。  
  
 `pcNumChars`  
 \[in\]中的字符数文档中的。  如果此参数是NULL，方法不返回值。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法返回行的字符数和数字文档中的。  
  
## 请参阅  
 [IDebugDocumentText 接口](../../winscript/reference/idebugdocumenttext-interface.md)