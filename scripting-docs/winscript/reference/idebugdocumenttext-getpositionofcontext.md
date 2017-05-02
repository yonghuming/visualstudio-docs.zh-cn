---
title: "IDebugDocumentText::GetPositionOfContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetPositionOfContext
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetPositionOfContext"
ms.assetid: 90fec730-c3fb-45fb-92ef-05ecc90dca38
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetPositionOfContext
返回字符位置大小与文档上下文相对应。  
  
## 语法  
  
```  
HRESULT GetPositionOfContext(  
   IDebugDocumentContext*  psc,  
   ULONG*                  pcCharacterPosition,  
   ULONG*                  cNumChars  
);  
```  
  
#### 参数  
 `psc`  
 \[in\]文档上下文对象。  
  
 `pcCharacterPosition`  
 \[in\]启动字符位置范围的位置。  
  
 `cNumChars`  
 \[in\]中的字符数。的大小。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 必须与文档上下文提供给此方法与此文档。  
  
## 请参阅  
 [IDebugDocumentText 接口](../../winscript/reference/idebugdocumenttext-interface.md)