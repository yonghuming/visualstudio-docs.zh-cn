---
title: "IActiveScriptSite::OnStateChange | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnStateChange
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnStateChange"
ms.assetid: 3e9c5cbe-ca8e-426a-84fd-04e9c2daac7e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSite::OnStateChange
通知宿主脚本引擎更改状态。  
  
## 语法  
  
```  
HRESULT OnStateChange(  
    SCRIPTSTATE ssScriptState  // new state of engine  
);  
```  
  
#### 参数  
 `ssScriptState`  
 \[in\]请值指示新脚本的状态。  有关状态的声明参见 [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) 方法。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  
  
## 请参阅  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)