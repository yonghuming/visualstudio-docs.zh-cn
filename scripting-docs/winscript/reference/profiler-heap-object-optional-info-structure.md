---
title: "PROFILER_HEAP_OBJECT_OPTIONAL_INFO 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 77e638bd-ae36-4292-a170-90a0c500e610
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# PROFILER_HEAP_OBJECT_OPTIONAL_INFO 结构
表示有关堆对象的可选信息。  
  
## 语法  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_OPTIONAL_INFO  
{  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE infoType;  
    [switch_type(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE), switch_is(infoType)] union  
    {  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE)] PROFILER_HEAP_OBJECT_ID prototype;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME)] LPCWSTR functionName;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE)] UINT elementAttributesSize;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE)] UINT elementTextChildrenSize;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST)] PROFILER_HEAP_OBJECT_SCOPE_LIST* scopeList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY)] PROFILER_HEAP_OBJECT_RELATIONSHIP* internalProperty;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* namePropertyList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* indexPropertyList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* relationshipList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* eventList;  
    };  
} PROFILER_HEAP_OBJECT_OPTIONAL_INFO;  
  
```  
  
## 成员  
  
|成员|类型|说明|  
|--------|--------|--------|  
|infoType|[PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_TYPE 枚举](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|可选信息的类型。|  
|Prototype — 原型|[PROFILER\_HEAP\_OBJECT\_ID 类型](../../winscript/reference/profiler-heap-object-id-type.md)|堆对象的原型对象的ID。|  
|functionName|LPCWSTR|堆对象的函数的名称。|  
|elementAttributesSize|UINT|堆对象的元素属性的范围。|  
|elementTextChildrenSize|UINT|堆对象的文本子级大小。|  
|scopeList|[PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST 结构](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|堆对象的范围列表。|  
|internalProperty|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP 结构](../../winscript/reference/profiler-heap-object-relationship-structure.md)|堆对象的内部属性。|  
|namePropertyList|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST 结构](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|堆对象名属性的列表。|  
|indexPropertyList|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST 结构](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|堆对象的索引属性的列表。|  
|relationshipList|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST 结构](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|堆对象的关系的列表。|  
|eventList|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST 结构](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|堆对象的事件的列表。|