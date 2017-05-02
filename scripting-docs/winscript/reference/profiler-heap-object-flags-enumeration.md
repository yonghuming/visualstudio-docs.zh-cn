---
title: "PROFILER_HEAP_OBJECT_FLAGS 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 0f517743-cc4a-4911-add3-a43680071a1f
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# PROFILER_HEAP_OBJECT_FLAGS 枚举
表示有关堆对象的基本信息的标志。  使用在 [PROFILER\_HEAP\_OBJECT 结构](../../winscript/reference/profiler-heap-object-structure.md)。  
  
## 语法  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_OBJECT_FLAGS_NEW_OBJECT            = 0x00000001,  
    PROFILER_HEAP_OBJECT_FLAGS_IS_ROOT               = 0x00000002,  
    PROFILER_HEAP_OBJECT_FLAGS_SITE_CLOSED           = 0x00000004,  
    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL              = 0x00000008,  
    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_UNKNOWN      = 0x00000010,  
    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_DISPATCH     = 0x00000020,  
    PROFILER_HEAP_OBJECT_FLAGS_SIZE_APPROXIMATE      = 0x00000040,  
    PROFILER_HEAP_OBJECT_FLAGS_SIZE_UNAVAILABLE      = 0x00000080,  
    PROFILER_HEAP_OBJECT_FLAGS_NEW_STATE_UNAVAILABLE = 0x00000100,  
    PROFILER_HEAP_OBJECT_FLAGS_WINRT_INSTANCE        = 0x00000200,  
    PROFILER_HEAP_OBJECT_FLAGS_WINRT_RUNTIMECLASS    = 0x00000400,  
    PROFILER_HEAP_OBJECT_FLAGS_WINRT_DELEGATE        = 0x00000800,  
    PROFILER_HEAP_OBJECT_FLAGS_WINRT_NAMESPACE       = 0x00001000,  
} PROFILER_HEAP_OBJECT_FLAGS;  
  
```  
  
## 成员  
  
|成员|值|说明|  
|--------|-------|--------|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_NEW\_OBJECT|0x00000001|分配了此堆对象，以前的堆枚举请求之后。  [PROFILER\_HEAP\_OBJECT\_ID 类型](../../winscript/reference/profiler-heap-object-id-type.md) 值，如果对象集合，可以重用。|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_IS\_ROOT|0x00000002|此堆对象是对象图的根对象。|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_SITE\_CLOSED|0x00000004|此堆对象是从关闭的脚本站点。|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_EXTERNAL|0x00000008|此堆对象在JavaScript垃圾回收堆之外分配了。|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_EXTERNAL\_UNKNOWN|0x00000010|此堆对象在垃圾回收堆之外分配并实现IUnknown。|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_EXTERNAL\_DISPATCH|0x00000020|此堆对象在垃圾回收堆之外分配并实现IDISPATCH接口。|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_SIZE\_APPROXIMATE|0x00000040|此对象堆的大小是近似的。|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_SIZE\_UNAVAILABLE|x00000080|此对象堆的大小不可用。|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_WINRT\_INSTANCE|0x00000200|堆对象是Windows运行时实例。|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_WINRT\_RUNTIMECLASS|0x00000400|堆对象是Windows运行时运行时选件类。|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_WINRT\_DELEGATE|0x00000800|堆对象是Windows运行时委托。|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_WINRT\_NAMESPACE|0x00001000|堆对象在Windows运行时命名空间。|