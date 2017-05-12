---
title: "IDebugDocumentText::GetLineOfPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetLineOfPosition
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetLineOfPosition"
ms.assetid: fe8d4802-ea16-49ca-8973-89dcaf6c915b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetLineOfPosition
返回行号，因此，可选择，字符按对应于特定字符位置的行中。  
  
## 语法  
  
```  
HRESULT GetLineOfPosition(  
   ULONG   cCharacterPosition,  
   ULONG*  pcLineNumber,  
   ULONG*  pcCharacterOffsetInLine  
);  
```  
  
#### 参数  
 `cCharacterPosition`  
 \[in\]启动字符位置范围的位置。  
  
 `pcLineNumber`  
 \[out\] 范围的行号。  
  
 `pcCharacterOffsetInLine`  
 \[in, out\] 范围的字符按行 `pcLineNumber`。  如果此参数是 `NULL`，方法不返回值。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法返回行号，因此，可选择，字符按对应于特定字符位置的行中。  
  
## 请参阅  
 [IDebugDocumentText 接口](../../winscript/reference/idebugdocumenttext-interface.md)