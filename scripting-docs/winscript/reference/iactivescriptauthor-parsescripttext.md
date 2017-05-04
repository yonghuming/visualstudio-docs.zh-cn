---
title: "IActiveScriptAuthor::ParseScriptText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.ParseScriptText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::ParseScriptText"
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthor::ParseScriptText
分析脚本文本，添加文本到生成引擎的脚本，并创建对应于该脚本块的 `IScriptEntry` 对象。  
  
## 语法  
  
```  
HRESULT ParseScriptText(  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### 参数  
 `pszCode`  
 \[in\]分析的脚本文本。  
  
 `pszItemName`  
 \[in\]包含项目名称与该脚本的缓冲区地址块。  
  
 `pszDelimiter`  
 \[in\]关闭脚本块分隔符的地址。  当 `pszCode` 从文本时流进行分析，宿主通常使用一个分隔符\(例如两个单引号\)，检测末尾的脚本块。  如果未标识末尾的分隔符的脚本块，将此参数设置为NULL。  
  
 `dwCookie`  
 \[in\]与新 `IScriptEntry` 对象的应用程序定义的值。  
  
 `dwFlags`  
 \[in\] 未使用。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
  
## 请参阅  
 [IActiveScriptAuthor 接口](../../winscript/reference/iactivescriptauthor-interface.md)