---
title: "PROFILER_HEAP_OBJECT 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 9f35362c-6856-4cfb-b990-031a156a58eb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_HEAP_OBJECT 结构
表示 [IActiveScriptProfilerControl3::EnumHeap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)收集的堆对象。  
  
## 语法  
  
```  
typedef struct _PROFILER_HEAP_OBJECT  
{  
    UINT size;  
    union {  
        PROFILER_HEAP_OBJECT_ID objectId;  
        PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;  
    };  
    PROFILER_HEAP_OBJECT_NAME_ID typeNameId;  
    USHORT flags;   
    USHORT optionalInfoCount;  
} PROFILER_HEAP_OBJECT;  
```  
  
## 成员  
  
|成员|类型|说明|  
|--------|--------|--------|  
|objectId|[PROFILER\_HEAP\_OBJECT\_ID 类型](../../winscript/reference/profiler-heap-object-id-type.md)|堆对象的ID。|  
|externalObjectAddress|[PROFILER\_EXTERNAL\_OBJECT\_ADDRESS 类型](../../winscript/reference/profiler-external-object-address-type.md)|对象的外部对象地址，如c. C\+\+分配对象，该对象是在JavaScript堆外。|  
|typeNameId|[PROFILER\_HEAP\_OBJECT\_NAME\_ID 类型](../../winscript/reference/profiler-heap-object-name-id-type.md)|堆目标类型名称的ID，检索从 [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)。  只有一个 `externalObjectAddress` 或 `typeName` 基于 `flags` 值存在。|  
|标志|[PROFILER\_HEAP\_OBJECT\_FLAGS 枚举](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|包含有关堆对象的基本信息的标志。|  
|optionalInfoCount|USHORT|的 [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO 结构](../../winscript/reference/profiler-heap-object-optional-info-structure.md) 记录数。堆对象可用。|