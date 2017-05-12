---
title: "SCRIPTTHREADSTATE 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: SCRIPTTHREADSTATE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SCRIPTTHREADSTATE 枚举"
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# SCRIPTTHREADSTATE 枚举
在一个脚本引擎指定线程的状态。  此枚举由 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) 方法使用。  
  
## 语法  
  
```  
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## 枚举值  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE\_NOTINSCRIPT|指定的线程不为一个为其编写脚本的任务，当前进程立即执行的脚本文本或不运行脚本宏。|  
|SCRIPTTHREADSTATE\_RUNNING|指定的线程对一个为其编写脚本的任务，用来处理立即执行的脚本文本或运行脚本宏。|  
  
## 请参阅  
 [活动脚本常量、枚举和错误代码](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)