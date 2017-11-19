---
title: "IActiveScriptProfilerHeapEnum 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 16756d0e-547a-4825-8b7b-a7e0e4708a04
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4761e8c7d4cc9c3372c7906e1503b8dbd059ca33
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilerheapenum-interface"></a>IActiveScriptProfilerHeapEnum 接口
堆集上的迭代器对象使用脚本引擎时，通过收集关联[iactivescriptprofilercontrol3:: Enumheap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)。  
  
## <a name="syntax"></a>语法  
  
```vb  
interface IActiveScriptProfilerHeapEnum : IUnknown  
```  
  
## <a name="methods"></a>方法  
 [IActiveScriptProfilerHeapEnum::Next 方法](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)  
 获取下一个对象中的一套所收集的堆对象[iactivescriptprofilercontrol3:: Enumheap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)。  
  
 [IActiveScriptProfilerHeapEnum::GetOptionalInfo 方法](../../winscript/reference/iactivescriptprofilerheapenum-getoptionalinfo-method.md)  
 获取指定对象上的可选信息中的一套所收集的堆对象[iactivescriptprofilercontrol3:: Enumheap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)。  
  
 [IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo 方法](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md)  
 释放指定[PROFILER_HEAP_OBJECT 结构](../../winscript/reference/profiler-heap-object-structure.md)结构和与其相关联[PROFILER_HEAP_OBJECT_OPTIONAL_INFO 结构](../../winscript/reference/profiler-heap-object-optional-info-structure.md)元素。  
  
 [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)  
 返回对应的字符串名称[PROFILER_HEAP_OBJECT_NAME_ID 类型](../../winscript/reference/profiler-heap-object-name-id-type.md)值...