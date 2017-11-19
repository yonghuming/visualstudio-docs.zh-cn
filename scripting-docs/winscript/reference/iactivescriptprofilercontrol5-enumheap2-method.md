---
title: "Iactivescriptprofilercontrol5:: Enumheap2 方法 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c493acdb2843877c506d9d84e145a79ac2d60d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol5enumheap2-method"></a>IActiveScriptProfilerControl5::EnumHeap2 方法
返回一个接口 ([IActiveScriptProfilerHeapEnum 接口](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) 可用来循环访问的关联的脚本引擎的上下文中的 GC 堆对象。  
  
 你可以在任一调试调用此方法或释放模式。 在 UI 线程处于空闲状态时，应调用此方法。 调用该方法后，应针对除外的脚本引擎执行任何操作[iactivescriptprofilerheapenum:: Next 方法](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)直到[iactivescriptprofilerheapenum:: Next 方法](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)返回 S_FALSE 或[IActiveScriptProfilerHeapEnum 接口](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)发布接口指针。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT EnumHeap2(    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>参数  
 enumFlags  
 值，该值指定是否公开了有关在对象关系指向的对象的额外信息。 额外的信息可能指明指向的对象是否为 getter 或 setter 方法。 有关详细信息，请参阅[PROFILER_HEAP_ENUM_FLAGS 枚举](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)。  
  
 ppEnum  
 [out]返回[IActiveScriptProfilerHeapEnum 接口](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)。  
  
## <a name="return-value"></a>返回值  
 返回一个 HRESULT。 可能的值如下：  
  
|返回值|含义|  
|------------------|-------------|  
|`S_OK`|已成功完成堆枚举。|  
|`E_OUTOFMEMORY`|没有足够的内存可用于执行堆枚举。|  
|`E_FAIL`|出现内部错误。|