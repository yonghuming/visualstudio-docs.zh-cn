---
title: "IActiveScriptProfilerCallback2::OnFunctionExitByName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerCallback2::OnFunctionExitByName"
ms.assetid: a6ddead4-e66d-4789-b778-84e5c343f908
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerCallback2::OnFunctionExitByName
通知探查器对象执行的脚本引擎运行文档对象模型\(DOM\)函数调用。  
  
## 语法  
  
```  
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### 参数  
 `pwszFunctionName`  
 \[out\]所使用的函数的名称脚本引擎完成运行。  
  
 `scriptType`  
 \[in\]函数的类型。  有关有效值的说明，请参见 [PROFILER\_SCRIPT\_TYPE 枚举](../../winscript/reference/profiler-script-type-enumeration.md)。  
  
## 返回值  
 此方法的返回值由脚本引擎忽略。  
  
## 备注  
 对DOM调用，脚本引擎调用此方法而不是调用 [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)。  这是由于大量的唯一方法和属性在DOM。  
  
## 请参阅  
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2 接口](../../winscript/reference/iactivescriptprofilercallback2-interface.md)