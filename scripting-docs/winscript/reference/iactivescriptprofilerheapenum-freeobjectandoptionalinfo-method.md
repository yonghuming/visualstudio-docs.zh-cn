---
title: "IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fdd5f7cc-be4e-4c13-a181-6320d26b44eb
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo 方法
释放指定的 [PROFILER\_HEAP\_OBJECT 结构](../../winscript/reference/profiler-heap-object-structure.md) framework及其关联的 [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO 结构](../../winscript/reference/profiler-heap-object-optional-info-structure.md) 元素。  
  
## 语法  
  
```  
HRESULT FreeObjectAndOptionalInfo (  
    [in] ULONG celt,  
    [in, size_is(celt)] PROFILER_HEAP_OBJECT** heapObjects);  
  
```  
  
#### 参数  
 `celt`  
 释放对象的数量。  
  
 `heapObjects`  
 [PROFILER\_HEAP\_OBJECT 结构](../../winscript/reference/profiler-heap-object-structure.md) 结构的数组。  
  
## 返回值  
 此 HRESULT。