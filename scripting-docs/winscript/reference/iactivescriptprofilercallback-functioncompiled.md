---
title: "IActiveScriptProfilerCallback::FunctionCompiled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.FunctionCompiled
apilocation: scrobj.dll
ms.assetid: a7e9ef17-3891-4731-9d08-c37bc489be61
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptProfilerCallback::FunctionCompiled
通知探查器对象脚本引擎遇到功能，在生成脚本时。  
  
## 语法  
  
```  
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### 参数  
 `functionId`  
 \[in\]函数的唯一ID。  此ID由脚本引擎分配。  
  
 `scriptId`  
 \[in\]脚本的唯一ID函数是的一部分。  
  
 `pwszFunctionName`  
 \[in\]功能或空名称匿名函数的。  
  
 `pwszFunctionNameHint`  
 \[in\]功能或空推断的名称，如果脚本引擎不推断任何名称。  
  
 `pIDebugDocumentContext`  
 \[out\]如果存在，对探查器必须为 [IDebugDocumentContext 接口](../../winscript/reference/idebugdocumentcontext-interface.md) 指针查询的 `IUnknown` 接口的指针。  否则为 null。  
  
## 返回值  
 此方法的返回值由脚本引擎忽略。  
  
## 备注  
 只有当由宿主，支持脚本引擎可提供文档上下文。  
  
## 请参阅  
 [IActiveScriptProfilerCallback 接口](../../winscript/reference/iactivescriptprofilercallback-interface.md)