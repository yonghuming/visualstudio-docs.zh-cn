---
title: "IActiveScriptProfilerControl 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptProfilerControl 接口
实现支持分析的脚本引擎。  通常，对象实现 `IActiveScriptProfilerControl` 还实现 [IActiveScript](../../winscript/reference/iactivescript.md) 接口。  在这种情况下，可以使用属性获取 `IActiveScriptProfilerControl` 接口通过调用对象的 `IUnknown::QueryInterface` 方法。  接口用于停止和启动分析提供必要的方法在脚本引擎。  
  
## 方法  
  
|方法|说明|  
|--------|--------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|分析在脚本引擎的开头。|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|将脚本引擎的探查器事件掩码。|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|停止分析在脚本引擎。|  
  
## 请参阅  
 [活动脚本探查器接口](../../winscript/reference/active-script-profiler-interfaces.md)