---
title: "活动脚本探查器常量、枚举和结构 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# 活动脚本探查器常量、枚举和结构
以下枚举事件使用脚本探查器接口。  
  
## 常数，枚举和结构  
  
|常量|描述|  
|--------|--------|  
|[PROFILER\_EXTERNAL\_OBJECT\_ADDRESS 类型](../../winscript/reference/profiler-external-object-address-type.md)|探查器的外部对象地址。  在 [PROFILER\_HEAP\_OBJECT 结构](../../winscript/reference/profiler-heap-object-structure.md) 和 [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP 结构](../../winscript/reference/profiler-heap-object-relationship-structure.md) 上使用。|  
|[PROFILER\_HEAP\_OBJECT\_ID 类型](../../winscript/reference/profiler-heap-object-id-type.md)|堆对象的ID。  在[PROFILER\_HEAP\_OBJECT 结构](../../winscript/reference/profiler-heap-object-structure.md) [PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST 结构](../../winscript/reference/profiler-heap-object-scope-list-structure.md), [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO 结构](../../winscript/reference/profiler-heap-object-optional-info-structure.md)，和[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP 结构](../../winscript/reference/profiler-heap-object-relationship-structure.md)上使用。|  
|[PROFILER\_HEAP\_OBJECT\_NAME\_ID 类型](../../winscript/reference/profiler-heap-object-name-id-type.md)|堆对象的名称的 ID。  在 [PROFILER\_HEAP\_OBJECT 结构](../../winscript/reference/profiler-heap-object-structure.md) 中使用。|  
  
|枚举|描述|  
|--------|--------|  
|[PROFILER\_EVENT\_MASK 枚举](../../winscript/reference/profiler-event-mask-enumeration.md)|指示应分析事件的类型。|  
|[PROFILER\_HEAP\_ENUM\_FLAGS 枚举](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|表示有关对象关系中指向的堆对象额外信息是否公开的标志。  在 [IActiveScriptProfilerControl5::EnumHeap2 方法](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)中使用。|  
|[PROFILER\_HEAP\_OBJECT\_FLAGS 枚举](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|表示有关堆对象的基本信息的标志。  在 [PROFILER\_HEAP\_OBJECT 结构](../../winscript/reference/profiler-heap-object-structure.md)中使用。|  
|[PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_TYPE 枚举](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|表示可选类型的信息。  在 [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO 结构](../../winscript/reference/profiler-heap-object-optional-info-structure.md) 中使用。|  
|[PROFILER\_RELATIONSHIP\_INFO 枚举](../../winscript/reference/profiler-relationship-info-enumeration.md)|在关系中表示有关对象的信息。  在 [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP 结构](../../winscript/reference/profiler-heap-object-relationship-structure.md) 中使用。|  
|[PROFILER\_SCRIPT\_TYPE 枚举](../../winscript/reference/profiler-script-type-enumeration.md)|指定脚本的类型。|  
  
|结构|描述|  
|--------|--------|  
|[PROFILER\_HEAP\_OBJECT 结构](../../winscript/reference/profiler-heap-object-structure.md)|用[IActiveScriptProfilerControl3::EnumHeap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)收集表示堆对象。|  
|[PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO 结构](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|表示有关堆对象的可选信息。|  
|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP 结构](../../winscript/reference/profiler-heap-object-relationship-structure.md)|表示堆对象的关系。|  
|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST 结构](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|表示属于堆对象关系的列表。|  
|[PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST 结构](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|此结构仅与函数对象有关联。  范围列表表示函数的关闭为每个大小与之关联的属性的堆对象列表，表示在每个特定范围的变量范围的列表。  在某些情况下，对象的名称在该范围内可能不可用，只能见 ID。|  
  
## 请参阅  
 [活动脚本探查器接口](../../winscript/reference/active-script-profiler-interfaces.md)