---
title: "IActiveScriptSite::OnEnterScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnEnterScript
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnEnterScript"
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnEnterScript
通知宿主脚本引擎开始执行脚本代码。  
  
## 语法  
  
```  
HRESULT OnEnterScript(void);  
```  
  
## 返回值  
 如果成功，则返回 `S_OK`。  
  
## 备注  
 脚本引擎必须对每个项或重新输入的此方法将脚本引擎中。  例如，在中，如果脚本调用然后触发脚本引擎处理的事件的对象，脚本引擎必须在执行该操作之前调用 `IActiveScriptSite::OnEnterScript`，并且必须调用 [IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) 方法在执行该操作之后，但在返回之前到激发该事件的对象。  调用此方法可以嵌套。  每个调用此方法需要相应调用 `IActiveScriptSite::OnLeaveScript`。  
  
## 请参阅  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)