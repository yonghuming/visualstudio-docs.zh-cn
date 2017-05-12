---
title: "IActiveScriptProfilerHeapEnum 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 16756d0e-547a-4825-8b7b-a7e0e4708a04
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptProfilerHeapEnum 接口
在堆对象的一个迭代器与脚本引擎，收集 [IActiveScriptProfilerControl3::EnumHeap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)。  
  
## 语法  
  
```vb  
interface IActiveScriptProfilerHeapEnum : IUnknown  
```  
  
## 方法  
 [IActiveScriptProfilerHeapEnum::Next 方法](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)  
 获取下一对象或在设置 [IActiveScriptProfilerControl3::EnumHeap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)收集的堆对象。  
  
 [IActiveScriptProfilerHeapEnum::GetOptionalInfo 方法](../../winscript/reference/iactivescriptprofilerheapenum-getoptionalinfo-method.md)  
 获取与指定对象的可选信息在设置 [IActiveScriptProfilerControl3::EnumHeap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)收集的堆对象。  
  
 [IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo 方法](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md)  
 释放指定的 [PROFILER\_HEAP\_OBJECT 结构](../../winscript/reference/profiler-heap-object-structure.md) framework及其关联的 [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO 结构](../../winscript/reference/profiler-heap-object-optional-info-structure.md) 元素。  
  
 [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)  
 返回字符串名称与 [PROFILER\_HEAP\_OBJECT\_NAME\_ID 类型](../../winscript/reference/profiler-heap-object-name-id-type.md) 值相对应。