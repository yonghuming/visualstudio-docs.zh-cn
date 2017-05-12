---
title: "IActiveScriptProfilerHeapEnum::Next 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 0336286f-1dcd-4df9-adf5-76b59b4e74bb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IActiveScriptProfilerHeapEnum::Next 方法
从 [IActiveScriptProfilerControl3::EnumHeap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)获取下一对象或在设置堆对象。  
  
## 语法  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] PROFILER_HEAP_OBJECT** heapObjects,   
    [out] ULONG *pceltFetched);  
  
```  
  
#### 参数  
 `celt`  
 要返回的对象数。  
  
 `heapObjects`  
 \[out\] [PROFILER\_HEAP\_OBJECT 结构](../../winscript/reference/profiler-heap-object-structure.md) 结构。  
  
 `pceltFetched`  
 \[in\]返回的对象的数目，  
  
## 返回值  
 此 HRESULT。