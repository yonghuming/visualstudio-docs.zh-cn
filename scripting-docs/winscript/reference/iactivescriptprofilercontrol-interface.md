---
title: "IActiveScriptProfilerControl 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0d598302ae78ca0b2a1e7c1f94c949800378a2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol-interface"></a>IActiveScriptProfilerControl 接口
由支持分析脚本引擎实现。 通常，实现的对象`IActiveScriptProfilerControl`还实现[IActiveScript](../../winscript/reference/iactivescript.md)接口。 在这种情况下，你可以获取的句柄`IActiveScriptProfilerControl`接口通过调用`IUnknown::QueryInterface`对象上的方法。 接口提供了有关停止和启动脚本引擎上进行分析所需的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|启动脚本引擎上进行分析。|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|设置脚本引擎中的探查器事件掩码。|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|停止脚本引擎上进行分析。|  
  
## <a name="see-also"></a>另请参阅  
 [Active Script Profiler 接口](../../winscript/reference/active-script-profiler-interfaces.md)