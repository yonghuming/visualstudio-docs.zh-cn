---
title: "IActiveScriptSiteInterruptPoll::QueryContinue | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteInterruptPoll.QueryContinue
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteInterruptPoll::QueryContinue"
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteInterruptPoll::QueryContinue
允许宿主指定脚本应停止。  
  
## 语法  
  
```  
HRESULT QueryContinue();  
```  
  
#### 参数  
 此方法没有参数。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|调用成功，并且宿主允许该脚本继续运行。|  
|`S_FALSE`|调用成功，并且宿主请求该脚本将终止。|  
  
## 备注  
 除非 `QueryContinue` 方法的返回值为 `S_OK`，承载脚本应停止。  `S_FALSE` 的返回值指示该脚本将终止的宿主显式请求。  
  
 一种多线程的宿主可以使用 `IActiveScript::InterruptScriptThread` 方法停止脚本。  
  
## 请参阅  
 [IActiveScriptSiteInterruptPoll 接口](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)