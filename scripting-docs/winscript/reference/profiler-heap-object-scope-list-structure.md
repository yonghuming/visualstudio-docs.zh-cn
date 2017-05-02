---
title: "PROFILER_HEAP_OBJECT_SCOPE_LIST 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 33ebaa31-0a35-47d5-a4e3-afd83e16f53e
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# PROFILER_HEAP_OBJECT_SCOPE_LIST 结构
此结构与仅函数对象。  范围列表表示函数的关闭为每个大小与之关联的属性的堆对象列表表示在每个特定范围的变量范围的列表。  在某些情况下，对象的名称在该范围内可能不可用，因此，只有其索引。属性中列出可用。  
  
## 语法  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_SCOPE_LIST  
{  
    UINT count;  
    [size_is(count)] PROFILER_HEAP_OBJECT_ID scopes[];  
} PROFILER_HEAP_OBJECT_SCOPE_LIST;  
  
```  
  
## 成员  
  
|成员|类型|说明|  
|--------|--------|--------|  
|count|UINT|范围数|  
|scopes|[PROFILER\_HEAP\_OBJECT\_ID 类型](../../winscript/reference/profiler-heap-object-id-type.md)|大小。|