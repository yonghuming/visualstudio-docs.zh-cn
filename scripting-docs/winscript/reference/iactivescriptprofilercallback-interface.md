---
title: "IActiveScriptProfilerCallback 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4dc4b9d4e3b1f83a37e64e3a85387fd378d3ca7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallback-interface"></a>IActiveScriptProfilerCallback 接口
提供脚本引擎用于发生事件时通知探查器对象的方法。 通过探查器对象来实现此接口。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|调用以初始化探查器对象，每当在脚本引擎启动时分析。|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|调用以释放并释放探查器对象，每当分析脚本引擎已停止。|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|通知探查器对象的脚本引擎编译该脚本。|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|通知探查器对象的脚本引擎编译脚本时遇到一个函数。|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|通知的脚本引擎是将要执行不是调用到文档对象模型 (DOM) 的函数调用的探查器对象。|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|通知探查器对象的脚本引擎完成执行函数调用不是调用到 DOM|  
  
## <a name="remarks"></a>备注  
 函数调用到文档对象模型 (DOM) 的通知由[IActiveScriptProfilerCallback2 接口](../../winscript/reference/iactivescriptprofilercallback2-interface.md)。  
  
> [!NOTE]
>  若要添加的功能来启动和停止分析运行脚本时，调用以下方法。 通过使用这些方法，你可以获取完整的调用堆栈，如果[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]时启动或停止分析运行。  
>   
>  -   调用[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)通知探查器已启动分析。  
> -   调用[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)通知探查器，你很快将停止分析。  
  
## <a name="see-also"></a>另请参阅  
 [Active Script Profiler 接口](../../winscript/reference/active-script-profiler-interfaces.md)