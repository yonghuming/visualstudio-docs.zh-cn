---
title: "IActiveScriptProfilerCallback::Shutdown | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.Shutdown
apilocation: scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptProfilerCallback::Shutdown
调用以通知探查器对象，只要分析在一个脚本引擎会停止。  这样，探查器对象可以调用其清理例程，则必须。  此方法由脚本引擎也称为，当脚本引擎关闭时关闭，或者，如果对 [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) 的调用失败时。  
  
## 语法  
  
```  
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### 参数  
 `hrReason`  
 \[in\]关闭的原因。  如果脚本引擎关闭，`S_OK` 通过。  如果对 [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) 的调用返回失败HRESULT，HRESULT通过。  否则，此值从 [IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)检索。  
  
## 返回值  
 此方法的返回值由脚本引擎忽略。  
  
## 请参阅  
 [IActiveScriptProfilerCallback 接口](../../winscript/reference/iactivescriptprofilercallback-interface.md)