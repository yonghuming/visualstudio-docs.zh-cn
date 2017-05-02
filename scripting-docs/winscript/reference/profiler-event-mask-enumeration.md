---
title: "PROFILER_EVENT_MASK 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: PROFILER_EVENT_MASK
apilocation: scrobj.dll
ms.assetid: c2168408-f4f6-4600-971d-f15b4edf4ca2
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# PROFILER_EVENT_MASK 枚举
指示应分析事件的类型。  
  
## 语法  
  
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
  
## 成员  
  
|成员|说明|  
|--------|--------|  
|PROFILER\_EVENT\_MASK\_TRACE\_SCRIPT\_FUNCTION\_CALL|分析在用户编写的脚本和动态代码的已定义功能。|  
|PROFILER\_EVENT\_MASK\_TRACE\_NATIVE\_FUNCTION\_CALL|分析由脚本引擎定义的本机函数。|  
|PROFILER\_EVENT\_MASK\_TRACE\_ALL|分析所有用户定义，并脚本函数的引擎，排除调入文档对象模型\(DOM\)。|  
|PROFILER\_EVENT\_MASK\_TRACE\_DOM\_FUNCTION\_CALL|分析调用到DOM的功能。|  
|PROFILER\_EVENT\_MASK\_TRACE\_ALL\_WITH\_DOM|分析所有功能，包括对DOM。|  
  
## 请参阅  
 [活动脚本探查器常量、枚举和结构](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)   
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)