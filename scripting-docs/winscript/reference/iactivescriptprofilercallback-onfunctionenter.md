---
title: "IActiveScriptProfilerCallback::OnFunctionEnter | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.OnFunctionEnter
apilocation: scrobj.dll
ms.assetid: 12dab2b4-df4e-444d-99cb-25e1c278e6e8
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptProfilerCallback::OnFunctionEnter
通知探查器对象脚本引擎将执行不是对文档对象模型\(DOM\)的函数调用。  
  
## 语法  
  
```  
HRESULT OnFunctionEnter(  
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
 对DOM调用，脚本引擎调用 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) 而不是 `IActiveScriptProfilerCallback::OnFunctionEnter`。  这是由于大量的唯一方法和属性在DOM。  
  
## 请参阅  
 [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)   
 [IActiveScriptProfilerCallback 接口](../../winscript/reference/iactivescriptprofilercallback-interface.md)