---
title: "IActiveScriptProfilerHeapEnum::GetOptionalInfo 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptProfilerHeapEnum::GetOptionalInfo 方法
获取指定对象上的可选信息（设置堆中的对象从返回[IActiveScriptProfilerControl3::EnumHeap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)\)。  
  
 不应释放返回的内存分配给返回的对象。  而应调用 [IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo 方法](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md)。  
  
## 语法  
  
```  
HRESULT GetOptionalInfo (  
    [in] PROFILER_HEAP_OBJECT* heapObject,  
    [in] ULONG celt,  
    [out, size_is(celt)] PROFILER_HEAP_OBJECT_OPTIONAL_INFO* optionalInfo);  
  
```  
  
#### 参数  
 `heapObject`  
 要返回其信息的 [PROFILER\_HEAP\_OBJECT 结构](../../winscript/reference/profiler-heap-object-structure.md)。  
  
 `celt`  
 要在中返回的 [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO 结构](../../winscript/reference/profiler-heap-object-optional-info-structure.md) 结构的数目。  
  
 `optionalInfo`  
 \[out\][PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO 结构](../../winscript/reference/profiler-heap-object-optional-info-structure.md) 的结构为指定的对象。  
  
## 返回值  
 此 HRESULT。