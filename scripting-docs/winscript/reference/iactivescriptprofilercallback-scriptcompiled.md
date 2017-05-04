---
title: "IActiveScriptProfilerCallback::ScriptCompiled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.ScriptCompiled
apilocation: scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptProfilerCallback::ScriptCompiled
通知探查器对象脚本引擎编译的脚本。  此方法针对生成的每个脚本调用。  
  
## 语法  
  
```  
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### 参数  
 `scriptId`  
 \[in\]生成脚本的唯一ID。  此ID由脚本引擎分配。  
  
 `type`  
 \[in\]生成脚本的类型。  值在 [PROFILER\_SCRIPT\_TYPE 枚举](../../winscript/reference/profiler-script-type-enumeration.md)定义。  
  
 `pIDebugDocumentContext`  
 \[out\]如果存在，对探查器必须为 [IDebugDocumentContext 接口](../../winscript/reference/idebugdocumentcontext-interface.md) 指针查询的 `IUnknown` 接口的指针。  否则，这将为空。  
  
## 返回值  
 此方法的返回值由脚本引擎忽略。  
  
## 备注  
 只有当由宿主，支持脚本引擎可提供文档上下文。  
  
## 请参阅  
 [IActiveScriptProfilerCallback 接口](../../winscript/reference/iactivescriptprofilercallback-interface.md)