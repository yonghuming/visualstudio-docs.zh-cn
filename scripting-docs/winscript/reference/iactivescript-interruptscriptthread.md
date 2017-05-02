---
title: "IActiveScript::InterruptScriptThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.InterruptScriptThread
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_InterruptScriptThread"
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::InterruptScriptThread
中断运行的脚本线程\(事件接收器、立即执行或宏调用\)的执行。  此方法可用于停止例如承受不住的脚本\(，陷入无穷循环\)。  它可以从非基础线程调用未导致非基础出站承载对象或到 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 方法。  
  
## 语法  
  
```  
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### 参数  
 `stidThread`  
 \[in\]中断线程的ID或一个以下特殊线程标识符值：  
  
|值|含义|  
|-------|--------|  
|SCRIPTTHREADID\_ALL|所有线程。  该中断当前应用于正在进行任何脚本的方法。  请注意，除非调用方请求该脚本是分开的，下一个为其编写脚本的事件会导致脚本代码再次调用与设置为的SCRIPTSTATE\_DISCONNECTED或SCRIPTSTATE\_INITIALIZED标志的 [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) 方法来运行。|  
|SCRIPTTHREADID\_BASE|基本线程;即脚本引擎实例化的线程。|  
|SCRIPTTHREADID\_CURRENT|当前执行线程。|  
  
 `pexcepinfo`  
 \[in\]包含应改为中止的脚本报告错误的信息的 `EXCEPINFO` 结构的地址。  
  
 `dwFlags`  
 \[in\]可选标志与该中断。  可以是这些值之一：  
  
|值|含义|  
|-------|--------|  
|SCRIPTINTERRUPT\_DEBUG|如果支持，输入脚本引擎的调试器在当前脚本执行点。|  
|SCRIPTINTERRUPT\_RAISEEXCEPTION|如果支持脚本引擎的语言，使脚本处理异常。  否则，脚本方法中止，并将错误代码返回调用方;即事件源或宏祈求者。|  
  
## 返回值  
 返回下列值之一：  
  
|返回值|含义|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|参数无效。|  
|`E_POINTER`|无效指针指定了。|  
|`E_UNEXPECTED`|调用非预期\(例如，脚本引擎尚未加载还未初始化\)。|  
  
## 请参阅  
 [IActiveScript](../../winscript/reference/iactivescript.md)