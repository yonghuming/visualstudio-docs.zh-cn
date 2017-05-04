---
title: "IActiveScriptAuthor::GetEventHandler | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetEventHandler
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetEventHandler"
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptAuthor::GetEventHandler
返回具有指定的属性的scriptlet。  
  
## 语法  
  
```  
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### 参数  
 `pdisp`  
 \[in\]对应于 `NamedItem` scriptlet附加 `IDispatch` 对象。  
  
 `pszItem`  
 \[in\]完全限定scriptlet名称的顶部标识符的缓冲区地址在主机上。  
  
 `pszSubItem`  
 \[in\]完全限定scriptlet名称的第二级标识符的缓冲区地址在主机上。  设置为NULL，如果该名称只有一个级别。  
  
 `pszEvent`  
 \[in\]一个缓冲区的地址。  scriptlet是此事件的事件处理程序。  
  
 `ppse`  
 \[in\]接收指向该scriptlet `IScriptEntry` 接口具有指定的属性变量的地址。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
  
## 请参阅  
 [IActiveScriptAuthor 接口](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IScriptEntry 接口](../../winscript/reference/iscriptentry-interface.md)