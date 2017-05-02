---
title: "IActiveScriptProfilerControl5::EnumHeap2 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IActiveScriptProfilerControl5::EnumHeap2 方法
返回可用于在关联的脚本引擎上下文中迭代访问 GC 堆对象的接口 \([IActiveScriptProfilerHeapEnum 接口](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\)。  
  
 在调试或发布模式中可以调用此方法。  当 UI 线程空闲时，应调用此方法。  在调用方法之后，不应执行操作除 [IActiveScriptProfilerHeapEnum::Next 方法](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) 外的脚本引擎，直到 [IActiveScriptProfilerHeapEnum::Next 方法](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) 返回 S\_FALSE 或释放 [IActiveScriptProfilerHeapEnum 接口](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) 接口指针。  
  
## 语法  
  
```  
HRESULT EnumHeap2(  
    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,  
    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
  
```  
  
#### 参数  
 enumFlags  
 值用于指定有关对象关系中指向的对象的额外信息是否公开。  附加信息可能指示所指向的对象是否是一个 getter 或 setter 方法。  有关更多信息，请参见 [PROFILER\_HEAP\_ENUM\_FLAGS 枚举](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)。  
  
 ppEnum  
 \[out\] 返回 [IActiveScriptProfilerHeapEnum 接口](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)。  
  
## 返回值  
 返回 HRESULT。  可能值如下：  
  
|返回值|含义|  
|---------|--------|  
|`S_OK`|成功完成堆枚举。|  
|`E_OUTOFMEMORY`|没有足够的内存执行堆枚举。|  
|`E_FAIL`|出现内部错误。|