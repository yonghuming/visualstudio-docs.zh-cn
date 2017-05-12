---
title: "PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1a41b642-c9a9-4d83-b943-d59b232eebf6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS 枚举
表示对象关系中指向的堆对象是否为 getter 或 setter 方法的标志。  使用在 [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) 方法时，PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS 值。`enumFlags` 参数指定。  
  
## 语法  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,  
    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,  
    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,  
} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
  
```  
  
## 成员  
  
|成员|值|描述|  
|--------|-------|--------|  
|PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS\_NONE|0x00000000|对象关系中指向的该堆对象既不被标识为 getter 方法也不被标识为 setter 方法。|  
|PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS\_IS\_GET\_ACCESSOR|0x00010000|对象关系中指向的堆对象是 getter 方法。  此信息在高将存储 2 个字节 \(16 位\) [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) 字段。|  
|PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS\_IS\_SET\_ACCESSOR|0x00020000|对象关系中指向的堆对象是 setter 方法。  此信息在高将存储 2 个字节 \(16 位\) `PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo` 字段。|