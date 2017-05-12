---
title: "IActiveScriptProfilerCallback::OnFunctionExit | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.OnFunctionExit
apilocation: scrobj.dll
ms.assetid: a5d21715-2b0b-423e-8644-f04a9e7cde3d
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptProfilerCallback::OnFunctionExit
通知探查器对象执行的脚本引擎执行不是对文档对象模型\(DOM\)的函数调用。  
  
## 语法  
  
```  
HRESULT OnFunctionExit(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### 参数  
 `scriptId`  
 \[in\]脚本的唯一ID函数是的一部分。  此ID由脚本引擎分配。  
  
 `functionId`  
 \[in\]函数的唯一ID。  此ID由脚本引擎分配。  
  
## 返回值  
 此方法的返回值由脚本引擎忽略。  
  
## 备注  
 对DOM调用，脚本引擎调用 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md) 而不是 `IActiveScriptProfilerCallback::OnFunctionExit`。  这是由于大量的唯一方法和属性在DOM。  
  
## 请参阅  
 [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)   
 [IActiveScriptProfilerCallback 接口](../../winscript/reference/iactivescriptprofilercallback-interface.md)