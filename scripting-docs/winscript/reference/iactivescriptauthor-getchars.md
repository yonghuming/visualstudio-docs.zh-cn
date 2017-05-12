---
title: "IActiveScriptAuthor::GetChars | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetChars
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetChars"
ms.assetid: a73ba263-12f7-4d5f-b4c8-9ad7e2d5d3cb
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IActiveScriptAuthor::GetChars
返回设置请求的完成上下文的完成字符。  
  
## 语法  
  
```  
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### 参数  
 `fRequestedList`  
 \[in\]请求完成的上下文。  
  
|常量|值|说明|  
|--------|-------|--------|  
|SCRIPT\_CMPL\_ENUM\_TRIGGER|0x0001|请求的左侧枚举。|  
|SCRIPT\_CMPL\_MEMBER\_TRIGGER|0x0002|请求成员完成上下文。|  
|SCRIPT\_CMPL\_PARAM\_TRIGGER|0x0003|请求参数列表。|  
|SCRIPT\_CMPL\_COMMIT|0x0004|请求的完成列表。|  
  
 `pbstrChars`  
 \[in\]对应于请求的完成上下文的字符。  
  
|`fRequestedList` 参数|返回的字符|  
|-------------------------|-----------|  
|SCRIPT\_CMPL\_ENUM\_TRIGGER|“.”|  
|SCRIPT\_CMPL\_MEMBER\_TRIGGER|“\=”|  
|SCRIPT\_CMPL\_PARAM\_TRIGGER|\(“，”|  
|SCRIPT\_CMPL\_COMMIT|“\(\)”|  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
  
## 请参阅  
 [IActiveScriptAuthor 接口](../../winscript/reference/iactivescriptauthor-interface.md)