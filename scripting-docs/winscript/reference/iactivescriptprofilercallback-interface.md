---
title: "IActiveScriptProfilerCallback 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IActiveScriptProfilerCallback 接口
提供脚本引擎用于通知探查器对象的方法，当事件发生时。  此接口由探查器对象实现。  
  
## 方法  
  
|方法|说明|  
|--------|--------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|调用初始化探查器对象，只要分析在一个脚本引擎启动。|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|调用释放和释放探查器对象，只要分析在一个脚本引擎会停止。|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|通知探查器对象脚本引擎编译该脚本。|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|通知探查器对象脚本引擎遇到功能，在生成脚本时。|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|通知探查器对象脚本引擎将执行不是对文档对象模型\(DOM\)的函数调用。|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|通知探查器对象执行的脚本引擎执行不是对DOM的函数调用。|  
  
## 备注  
 函数调用文档对象模型\(DOM\) [IActiveScriptProfilerCallback2 接口](../../winscript/reference/iactivescriptprofilercallback2-interface.md)提供的通知。  
  
> [!NOTE]
>  若要添加能够启动和停止分析脚本时运行，请调用下列方法。  通过使用这些方法，您可以获取完整的调用堆栈，如果 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 运行，则启动或停止分析时。  
>   
>  -   调用 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) 通知探查器正在从启动分析。  
> -   调用 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) 通知探查器您很快将停止分析。  
  
## 请参阅  
 [活动脚本探查器接口](../../winscript/reference/active-script-profiler-interfaces.md)