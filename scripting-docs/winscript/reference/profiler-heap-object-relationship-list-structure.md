---
title: "PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 46ca87ea-5b0f-437d-a33f-b2d9a457e036
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST 结构
表示属于堆对象关系的列表。  
  
## 语法  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST  
{  
    UINT count;  
    [size_is(count)] PROFILER_HEAP_OBJECT_RELATIONSHIP elements[];  
} PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST;  
  
```  
  
## 成员  
  
|成员|类型|说明|  
|--------|--------|--------|  
|count|UINT|堆对象的关系的数目。|  
|elements|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP 结构](../../winscript/reference/profiler-heap-object-relationship-structure.md)|堆对象的关系。|