---
title: "IActiveScript::SetScriptState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.SetScriptState
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_SetScriptState"
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScript::SetScriptState
将脚本引擎到给定状态。  此方法可以从非基础线程调用未导致非基础出站承载对象或到 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 接口。  
  
## 语法  
  
```  
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### 参数  
 `ss`  
 \[in\]设置脚本引擎对给定状态。  将在 [SCRIPTSTATE 枚举](../../winscript/reference/scriptstate-enumeration.md) 枚举中定义的值之一。  
  
## 返回值  
 返回下列值之一：  
  
|返回值|含义|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_FAIL`|脚本引擎不支持该转换回该初始化状态。  宿主必须放弃此脚本引擎，以及创建和初始化加载新的脚本引擎获得相同的效果。|  
|`E_UNEXPECTED`|调用非预期\(例如，脚本引擎尚未加载还未初始化\)和非失败。|  
|`OLESCRIPT_S_PENDING`|方法成功排入队列，但是，该状态未更改。  在状态发生更改时，该网站。[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) 调用方法。|  
|`S_FALSE`|方法成功的，但是，该脚本已在给定状态。|  
  
## 备注  
 有关脚本引擎状态的更多信息，请参见 [Windows 脚本引擎](../../winscript/windows-script-engines.md) 的脚本引擎状态部分。  
  
## 请参阅  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)