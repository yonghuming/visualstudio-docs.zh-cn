---
title: "PROFILER_HEAP_OBJECT_RELATIONSHIP 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 3ab3d986-3314-4c7b-a1c8-18ed691a8b9c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_HEAP_OBJECT_RELATIONSHIP 结构
表示堆对象的关系。  
  
## 语法  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_RELATIONSHIP  
{  
    PROFILER_HEAP_OBJECT_NAME_ID relationshipId;  
    PROFILER_RELATIONSHIP_INFO relationshipInfo;  
    [switch_type(PROFILER_RELATIONSHIP_INFO), switch_is(relationshipInfo)] union  
    {  
        [case(PROFILER_PROPERTY_TYPE_NUMBER)] double numberValue;  
        [case(PROFILER_PROPERTY_TYPE_STRING)] LPCWSTR stringValue;  
        [case(PROFILER_PROPERTY_TYPE_HEAP_OBJECT)] PROFILER_HEAP_OBJECT_ID objectId;  
        [case(PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT)] PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;  
    };  
} PROFILER_HEAP_OBJECT_RELATIONSHIP;  
  
```  
  
## 成员  
  
|成员|值|说明|  
|--------|-------|--------|  
|relationshipId|[PROFILER\_HEAP\_OBJECT\_NAME\_ID 类型](../../winscript/reference/profiler-heap-object-name-id-type.md)|关系名称的ID，从 [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)。|  
|relationshipInfo|[PROFILER\_RELATIONSHIP\_INFO 枚举](../../winscript/reference/profiler-relationship-info-enumeration.md)|有关关系的信息。|  
|numberValue|double|数值。  只有一 `numberValue`\/`stringValue`\/`objectId`\/`externalObjectAddress` 基于 `relationshipInfo` 值设置，。|  
|stringValue|LPCWSTR|字符串值。|  
|objectId|[PROFILER\_HEAP\_OBJECT\_ID 类型](../../winscript/reference/profiler-heap-object-id-type.md)|堆对象的ID。|  
|externalObjectAddress|[PROFILER\_EXTERNAL\_OBJECT\_ADDRESS 类型](../../winscript/reference/profiler-external-object-address-type.md)|外部对象地址。|