---
title: "SCRIPTSTATE 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: SCRIPTSTATE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SCRIPTSTATE 枚举"
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# SCRIPTSTATE 枚举
指定一个脚本引擎的状态。  [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) 、 [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) 和 [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) 方法使用此枚举。  
  
## 语法  
  
```  
typedef enum tagSCRIPTSTATE {  
    SCRIPTSTATE_UNINITIALIZED = 0,  
    SCRIPTSTATE_INITIALIZED   = 5,  
    SCRIPTSTATE_STARTED       = 1,  
    SCRIPTSTATE_CONNECTED     = 2,  
    SCRIPTSTATE_DISCONNECTED  = 3,  
    SCRIPTSTATE_CLOSED        = 4  
} SCRIPTSTATE;  
```  
  
## 枚举值  
  
|||  
|-|-|  
|SCRIPTSTATE\_UNINITIALIZED|使用 `IPersist*` 接口和 [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)，脚本创建的，则，但未初始化。|  
|SCRIPTSTATE\_INITIALIZED|脚本初始化，则为;但不运行\(连接到其他对象或接收的事件\)也不执行任何代码。  代码可在执行查询通过调用 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md) 方法。|  
|SCRIPTSTATE\_STARTED|脚本可以执行代码，但是，不接收 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) 方法添加的对象事件。|  
|SCRIPTSTATE\_CONNECTED|脚本用于接收的事件已加载并连接。|  
|SCRIPTSTATE\_DISCONNECTED|脚本加载并具有一个运行时执行状态，但是，从接收的事件临时断开连接的。|  
|SCRIPTSTATE\_CLOSED|脚本已关闭。  脚本引擎不再工作并返回大多数方法是错误的。|  
  
## 请参阅  
 [活动脚本常量、枚举和错误代码](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)