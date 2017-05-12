---
title: "IActiveScriptAuthor::IsCommitChar | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.IsCommitChar
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::IsCommitChar"
ms.assetid: 7857c6f9-61e6-41e5-8e01-f56588c10421
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IActiveScriptAuthor::IsCommitChar
返回一个值特定字符是否应触发语句完成由应用程序进行。  
  
## 语法  
  
```  
HRESULT IsCommitChar(  
   OLECHAR    ch,  
   BOOL       *pfcommit  
);  
```  
  
#### 参数  
 `ch`  
 \[in\]测试的字符。  
  
 `pfcommit`  
 \[out\] `True`，如果字符是使字符;否则，`False`。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
  
## 请参阅  
 [IActiveScriptAuthor 接口](../../winscript/reference/iactivescriptauthor-interface.md)