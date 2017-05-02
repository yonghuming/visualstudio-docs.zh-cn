---
title: "IActiveScript::GetScriptState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptState
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptState"
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::GetScriptState
检索脚本引擎的当前状态。  此方法可以从非基础线程调用未导致非基础出站承载对象或到 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 接口。  
  
## 语法  
  
```  
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### 参数  
 `pss`  
 \[in\]接收值变量的地址。[SCRIPTSTATE 枚举](../../winscript/reference/scriptstate-enumeration.md) 枚举定义。  值指示脚本引擎的当前状态与调用线程。  
  
## 返回值  
 返回 `S_OK`，如果成功或 `E_POINTER`，如果无效指针指定了。  
  
## 请参阅  
 [IActiveScript](../../winscript/reference/iactivescript.md)