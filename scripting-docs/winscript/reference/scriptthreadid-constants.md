---
title: "SCRIPTTHREADID 常量 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: SCRIPTTHREADID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SCRIPTTHREADID"
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# SCRIPTTHREADID 常量
用于指定线程的类型。  
  
## 语法  
  
```  
typedef DWORD SCRIPTTHREADID;  
```  
  
## 常量  
  
|常量|值|含义|  
|--------|-------|--------|  
|SCRIPTTHREADID\_CURRENT|0xFFFFFFFD|当前执行线程。|  
|SCRIPTTHREADID\_BASE|0xFFFFFFFE|基本线程;即脚本引擎实例化的线程。|  
|SCRIPTTHREADID\_ALL|0xFFFFFFFF|所有线程。|  
  
## 备注  
 `IActiveScript::GetCurrentScriptThreadID`、 `IActiveScript::GetScriptThreadID`、 `IActiveScript::GetScriptThreadState`和 `IActiveScript::InterruptScriptThread`使用 `SCRIPTTHREADID` 类型，但是，常量可以由 `IActiveScript::GetScriptThreadState` 和 `IActiveScript::InterruptScriptThread`只使用。  
  
## 请参阅  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)