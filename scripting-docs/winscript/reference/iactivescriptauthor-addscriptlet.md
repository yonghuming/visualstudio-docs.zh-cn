---
title: "IActiveScriptAuthor::AddScriptlet | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.AddScriptlet
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::AddScriptlet"
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptAuthor::AddScriptlet
添加一个代码scriptlet作为根级别 `IScriptNode` 对象的子对象。  在宿主，scriptlet的完全限定名只允许具有两个级别。  
  
## 语法  
  
```  
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### 参数  
 `pszDefaultName`  
 \[in\]关联的默认名称的地址与scriptlet。  
  
 `pszCode`  
 \[in\] scriptlet文本的地址。  
  
 `pszItemName`  
 \[in\]完全限定scriptlet名称的顶部标识符的缓冲区地址在主机上。  
  
 `pszSubItemName`  
 \[in\]完全限定scriptlet名称的第二级标识符的缓冲区地址在主机上。  设置为NULL，如果该名称只有一个级别。  
  
 `pszEventName`  
 \[in\]一个scriptlet是一个事件处理程序缓冲区的地址。  
  
 `pszDelimiter`  
 \[in\]关闭脚本块分隔符的地址。  当 `pszCode` 从文本时流进行分析，宿主通常使用一个分隔符\(例如两个单引号\)，检测末尾的脚本块。  如果分隔符不指示末尾的脚本块，将此参数设置为NULL。  
  
 `dwCookie`  
 \[in\]用于将scriptlet与宿主对象的应用程序定义的值。  
  
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