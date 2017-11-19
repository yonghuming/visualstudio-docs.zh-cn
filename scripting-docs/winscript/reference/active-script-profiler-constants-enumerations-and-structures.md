---
title: "活动脚本探查器常量、 枚举和结构 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a37f64b14d0d732e48de66bb5268d47c95426937
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="active-script-profiler-constants-enumerations-and-structures"></a>活动脚本探查器常量、枚举和结构
活动脚本探查器接口使用以下枚举。  
  
## <a name="constants-enumerations-and-structures"></a>常量、枚举和结构  
  
|常量|描述|  
|---------------|-----------------|  
|[PROFILER_EXTERNAL_OBJECT_ADDRESS 类型](../../winscript/reference/profiler-external-object-address-type.md)|探查器外部对象地址。 在中使用[PROFILER_HEAP_OBJECT 结构](../../winscript/reference/profiler-heap-object-structure.md)和[PROFILER_HEAP_OBJECT_RELATIONSHIP 结构](../../winscript/reference/profiler-heap-object-relationship-structure.md)。|  
|[PROFILER_HEAP_OBJECT_ID 类型](../../winscript/reference/profiler-heap-object-id-type.md)|堆对象的 ID。 在中使用[PROFILER_HEAP_OBJECT 结构](../../winscript/reference/profiler-heap-object-structure.md)[PROFILER_HEAP_OBJECT_SCOPE_LIST 结构](../../winscript/reference/profiler-heap-object-scope-list-structure.md)， [PROFILER_HEAP_OBJECT_OPTIONAL_INFO 结构](../../winscript/reference/profiler-heap-object-optional-info-structure.md)，和[PROFILER_HEAP_OBJECT_RELATIONSHIP 结构](../../winscript/reference/profiler-heap-object-relationship-structure.md)。|  
|[PROFILER_HEAP_OBJECT_NAME_ID 类型](../../winscript/reference/profiler-heap-object-name-id-type.md)|堆对象的名称的 ID。 在中使用[PROFILER_HEAP_OBJECT 结构](../../winscript/reference/profiler-heap-object-structure.md)。|  
  
|枚举|描述|  
|------------------|-----------------|  
|[PROFILER_EVENT_MASK 枚举](../../winscript/reference/profiler-event-mask-enumeration.md)|指示应进行事件探查的事件的类型。|  
|[PROFILER_HEAP_ENUM_FLAGS 枚举](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|表示是否公开了有关在对象关系指向堆对象的额外信息的标志。 在中使用[iactivescriptprofilercontrol5:: Enumheap2 方法](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)。|  
|[PROFILER_HEAP_OBJECT_FLAGS 枚举](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|表示与堆对象有关的基本信息的标志。 在中使用[PROFILER_HEAP_OBJECT 结构](../../winscript/reference/profiler-heap-object-structure.md)。|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE 枚举](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|表示不同类型的可选信息。 在中使用[PROFILER_HEAP_OBJECT_OPTIONAL_INFO 结构](../../winscript/reference/profiler-heap-object-optional-info-structure.md)。|  
|[PROFILER_RELATIONSHIP_INFO 枚举](../../winscript/reference/profiler-relationship-info-enumeration.md)|表示关系中的对象有关的信息。 在中使用[PROFILER_HEAP_OBJECT_RELATIONSHIP 结构](../../winscript/reference/profiler-heap-object-relationship-structure.md)。|  
|[PROFILER_SCRIPT_TYPE 枚举](../../winscript/reference/profiler-script-type-enumeration.md)|指定脚本的类型。|  
  
|结构|描述|  
|----------------|-----------------|  
|[PROFILER_HEAP_OBJECT 结构](../../winscript/reference/profiler-heap-object-structure.md)|表示堆对象收集[iactivescriptprofilercontrol3:: Enumheap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)。|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO 结构](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|表示有关堆对象的可选信息。|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP 结构](../../winscript/reference/profiler-heap-object-relationship-structure.md)|表示堆对象的关系。|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST 结构](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|表示属于堆对象的关系的列表。|  
|[PROFILER_HEAP_OBJECT_SCOPE_LIST 结构](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|此结构是函数对象仅与相关联。 作用域列表表示函数的闭包为其中每个作用域是具有一个关联的属性列表，表示每个给定范围中的变量的堆对象的作用域的列表。 在某些情况下，可能不可用，该作用域中的对象的名称仅及其 id。|  
|[PROFILER_PROPERTY_TYPE_SUBSTRING_INFO 结构](../../winscript/reference/profiler-property-type-substring-info-structure.md)|表示有关类型的子字符串的信息。|  
  
## <a name="see-also"></a>另请参阅  
 [Active Script Profiler 接口](../../winscript/reference/active-script-profiler-interfaces.md)