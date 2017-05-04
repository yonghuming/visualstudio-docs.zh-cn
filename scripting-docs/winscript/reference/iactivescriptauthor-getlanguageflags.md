---
title: "IActiveScriptAuthor::GetLanguageFlags | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetLanguageFlags
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetLanguageFlags"
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# IActiveScriptAuthor::GetLanguageFlags
返回语言信息。  
  
## 语法  
  
```  
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### 参数  
 `pgrfasa`  
 \[in\]包含语言信息的标志。  可为下列值的组合：  
  
|常量|值|说明|  
|--------|-------|--------|  
|fasaPreferInternalHandler|0x0001|该语言由生成引擎的脚本愿意脚本事件处理程序创建而不是应用程序。|  
|fasaSupportInternalHandler|0x0002|该语言支持脚本该脚本创建的事件处理程序生成引擎。|  
|fasaCaseSensitive|0x0004|脚本语言区分大小写。|  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 如果生成引擎的脚本管理事件处理程序，应用程序应调用从 `IScriptEntry` 对象的 `CreateChildHandler`。  这将创建对应于事件处理程序中 `IScriptScriptlet` 对象。  该引擎还会将事件处理程序添加到脚本项。  事件处理程序是包含指定的签名信息的空功能。  
  
 如果您的应用程序管理事件处理程序，它应调用从表示事件处理程序scriptlet的 `IScriptNode` 对象的 `CreateChildHandler`。  这将创建与事件处理程序scriptlet的一 `IScriptScriptlet` 对象。  应用程序还必须添加一个空的函数用作事件处理程序添加到新的或现有的 `IScriptEntry` 对象。  
  
## 请参阅  
 [IActiveScriptAuthor 接口](../../winscript/reference/iactivescriptauthor-interface.md)