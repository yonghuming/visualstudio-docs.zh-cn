---
title: "PROFILER_SCRIPT_TYPE 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: PROFILER_SCRIPT_TYPE
apilocation: scrobj.dll
ms.assetid: 3ab6633a-6241-44f0-b837-14336f70c71e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# PROFILER_SCRIPT_TYPE 枚举
指定脚本的类型。  
  
## 语法  
  
```  
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## 成员  
  
|成员|说明|  
|--------|--------|  
|PROFILER\_SCRIPT\_TYPE\_USER|指定用户编写的脚本代码。|  
|PROFILER\_SCRIPT\_TYPE\_DYNAMIC|指定在执行时动态生成的脚本代码。|  
|PROFILER\_SCRIPT\_TYPE\_NATIVE|对于由脚本引擎定义的本机函数和对象指定脚本类型。|  
|PROFILER\_SCRIPT\_TYPE\_DOM|指定调入文档对象模型\(dom\) Internet Explorer \(DOM\)，例如，调用 `document.getElementById` 方法。|  
  
## 请参阅  
 [活动脚本探查器常量、枚举和结构](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)