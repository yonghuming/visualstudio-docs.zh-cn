---
title: "IActiveScript::GetScriptThreadID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptThreadID"
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScript::GetScriptThreadID
检索线程的一个脚本引擎中定义的标识符与特定Win32线程。  
  
## 语法  
  
```  
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### 参数  
 `dwWin32ThreadID` ,  
 \[in\]运行的Win32线程的线程标识符在当前进程的进程。  使用 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) 函数检索当前执行线程的线程标识符。  
  
 `pstidThread` ,  
 \[in\]接收脚本线程标识符与特定Win32线程变量的地址。  此标识符的解释留给脚本引擎，但是，它可以是Windows线程标识符的副本。  请注意，如果Win32线程终止，此标识符变得不指定，并且随后可以分配给另一个线程。  
  
## 返回值  
 返回下列值之一：  
  
|返回值|含义|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_POINTER`|无效指针指定了。|  
|`E_UNEXPECTED`|调用非预期\(例如，脚本引擎尚未加载还未初始化\)和非失败。|  
  
## 备注  
 该检索的标识符可用于对的后续调用脚本线程执行控件的方法\(如 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) 方法。  
  
 此方法可以从非基础线程调用未导致非基础出站承载对象或到 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) 接口。  
  
## 请参阅  
 [IActiveScript](../../winscript/reference/iactivescript.md)