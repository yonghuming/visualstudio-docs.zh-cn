---
title: "IActiveScriptProfilerCallback2::OnFunctionEnterByName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerCallback2::OnFunctionEnterByName"
ms.assetid: 24b1593a-97fc-4d70-9b85-ec86fb59f987
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptProfilerCallback2::OnFunctionEnterByName
通知探查器对象脚本引擎执行文档对象模型\(DOM\)函数调用。  
  
## 语法  
  
```  
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### 参数  
 `pwszFunctionName`  
 \[in\]脚本引擎执行函数的名称。  
  
 `scriptType`  
 \[in\]函数的类型。  有关有效值的说明，请参见 [PROFILER\_SCRIPT\_TYPE 枚举](../../winscript/reference/profiler-script-type-enumeration.md)。  
  
## 返回值  
 此方法的返回值由脚本引擎忽略。  
  
## 备注  
 对DOM调用，脚本引擎调用此方法而不是调用 [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)。  这是由于大量的唯一方法和属性在DOM。  
  
## 请参阅  
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)   
 [IActiveScriptProfilerCallback2 接口](../../winscript/reference/iactivescriptprofilercallback2-interface.md)