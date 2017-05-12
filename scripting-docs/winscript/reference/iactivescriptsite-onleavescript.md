---
title: "IActiveScriptSite::OnLeaveScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnLeaveScript
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnLeaveScript"
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnLeaveScript
通知宿主脚本引擎通过执行脚本代码返回。  
  
## 语法  
  
```  
HRESULT OnLeaveScript(void);  
```  
  
## 返回值  
 如果成功，则返回 `S_OK`。  
  
## 备注  
 脚本引擎必须在返回控件之前调用此方法将输入脚本引擎的调用的应用程序。  例如，在中，如果脚本调用然后触发脚本引擎处理的事件的对象，脚本引擎必须在执行该操作之前调用 [IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) 方法，并且必须在执行该操作之后调用 `IActiveScriptSite::OnLeaveScript` 在返回之前到激发该事件的对象。  调用此方法可以嵌套。  每个调用 `IActiveScriptSite::OnEnterScript` 需要相应调用此方法。  
  
## 请参阅  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)