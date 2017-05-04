---
title: "IActiveScriptProfilerCallback2 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerCallback2 接口"
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptProfilerCallback2 接口
提供脚本引擎用于通知探查器对象的方法，当文档对象模型\(DOM\)事件时。  此接口由探查器对象实现。  
  
## 方法  
  
|方法|说明|  
|--------|--------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|通知探查器对象脚本引擎运行DOM函数调用。|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|通知探查器对象执行的脚本引擎运行DOM函数调用。|  
  
## 备注  
 第一次发布的 `IActiveScriptProfilerCallback2` 接口与Internet Explorer 9。  
  
 的通知函数调用不是对DOM [IActiveScriptProfilerCallback 接口](../../winscript/reference/iactivescriptprofilercallback-interface.md)提供。  
  
> [!NOTE]
>  若要添加能够启动和停止分析脚本时运行，请调用下列方法。  通过使用这些方法，您可以获取完整的调用堆栈，如果 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 运行，则启动或停止分析时。  
>   
>  -   调用 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) 通知探查器正在从启动分析。  
> -   调用 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) 通知探查器您很快将停止分析。  
  
## 请参阅  
 [活动脚本探查器接口](../../winscript/reference/active-script-profiler-interfaces.md)