---
title: "IActiveScript::GetCurrentScriptThreadID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetCurrentScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetCurrentScriptThreadID"
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::GetCurrentScriptThreadID
检索当前正在执行的线程的一个脚本引擎中定义的标识符。  该标识符可用于对的后续调用脚本线程执行控件的方法\(如 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) 方法。  
  
## 语法  
  
```  
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### 参数  
 `pstidThread`  
 \[in\]接收脚本线程标识符变量的地址与当前线程关联。  此标识符的解释留给脚本引擎，但是，它可以是Windows线程标识符的副本。  如果Win32线程终止，此标识符变得不指定，并且随后可以分配给另一个线程。  
  
## 返回值  
 返回 `S_OK`，如果成功或 `E_POINTER`，如果无效指针指定了。  
  
## 备注  
 此方法可以从非基础线程调用未导致非基础出站承载对象或到 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 接口。  
  
## 请参阅  
 [IActiveScript](../../winscript/reference/iactivescript.md)