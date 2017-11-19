---
title: "IActiveScriptProfilerCallback2 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptProfilerCallback2 interface
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dc9fcd8ca4afec0fb474c0f3a7317b608c7c9f6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallback2-interface"></a>IActiveScriptProfilerCallback2 接口
提供脚本引擎用于文档对象模型 (DOM) 事件发生时通知探查器对象的方法。 通过探查器对象来实现此接口。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|通知脚本引擎要运行 DOM 函数调用的探查器对象。|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|通知探查器的脚本引擎的对象完成运行 DOM 函数调用。|  
  
## <a name="remarks"></a>备注  
 `IActiveScriptProfilerCallback2`首次发布与 Internet Explorer 9 的接口。  
  
 不是读入 DOM 的调用的函数调用的通知由[IActiveScriptProfilerCallback 接口](../../winscript/reference/iactivescriptprofilercallback-interface.md)。  
  
> [!NOTE]
>  若要添加的功能来启动和停止分析运行脚本时，调用以下方法。 通过使用这些方法，你可以获取完整的调用堆栈，如果[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]时启动或停止分析运行。  
>   
>  -   调用[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)通知探查器已启动分析。  
> -   调用[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)通知探查器，你很快将停止分析。  
  
## <a name="see-also"></a>另请参阅  
 [Active Script Profiler 接口](../../winscript/reference/active-script-profiler-interfaces.md)