---
title: "PROFILER_HEAP_ENUM_FLAGS 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 17936b7a-40d5-4774-b92b-b24ee391591e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_HEAP_ENUM_FLAGS 枚举
表示有关对象关系中指向的堆对象额外信息是否公开的标志。  使用在 [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) 方法。  
  
## 语法  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_ENUM_FLAGS_NONE                      = 0x00000000,  
    PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS  = 0x00000001,  
} PROFILER_HEAP_ENUM_FLAGS;  
  
```  
  
## 成员  
  
|成员|值|描述|  
|--------|-------|--------|  
|PROFILER\_HEAP\_ENUM\_FLAGS\_NONE|0x00000000|此堆对象不公开有关对象关系的附加信息。  此堆对象与 [IActiveScriptProfilerControl3::HeapEnum](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)的方式行为。|  
|PROFILER\_HEAP\_ENUM\_ENUM\_ STORE\_RELATIONSHIP\_FLAGS|0x00000001|此堆对象将公开关于对象关系指向的对象是否为 getter 方法或 setter 方法的信息。  此信息在高将存储 2 个字节 \(16 位\) [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) 字段作为一个 [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS](../../winscript/reference/profiler-heap-object-relationship-flags-enumeration.md) 枚举值。|