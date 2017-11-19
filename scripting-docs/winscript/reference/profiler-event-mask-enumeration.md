---
title: "PROFILER_EVENT_MASK 枚举 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: PROFILER_EVENT_MASK
apilocation: scrobj.dll
ms.assetid: c2168408-f4f6-4600-971d-f15b4edf4ca2
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68547fcb1fd2cd34b18a3d204baefd24d9da936b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="profilereventmask-enumeration"></a>PROFILER_EVENT_MASK 枚举
指示应进行事件探查的事件的类型。  
  
## <a name="syntax"></a>语法  
  
```  
typedef enum {  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL = 0x00000001,  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL = 0x00000002,  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL    = 0x00000004,  
    PROFILER_EVENT_MASK_TRACE_ALL =  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL |  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL,  
    PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM = PROFILER_EVENT_MASK_TRACE_ALL |  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL  
} PROFILER_EVENT_MASK;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL|配置文件在用户编写的脚本和动态代码中定义的函数。|  
|PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL|配置文件定义的脚本引擎的本机函数。|  
|PROFILER_EVENT_MASK_TRACE_ALL|配置文件的所有用户定义和脚本引擎函数，不包括到文档对象模型 (DOM) 的调用。|  
|PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL|调入 DOM 的配置文件函数|  
|PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM|配置文件包括到 DOM 的调用的所有函数|  
  
## <a name="see-also"></a>另请参阅  
 [活动脚本探查器常量、 枚举和结构](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)   
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)