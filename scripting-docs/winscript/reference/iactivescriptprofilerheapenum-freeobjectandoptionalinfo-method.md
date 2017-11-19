---
title: "Iactivescriptprofilerheapenum:: Freeobjectandoptionalinfo 方法 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fdd5f7cc-be4e-4c13-a181-6320d26b44eb
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 748e5dbc948cc22e084a4e0b1e13222174bb739e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilerheapenumfreeobjectandoptionalinfo-method"></a>IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo 方法
释放指定[PROFILER_HEAP_OBJECT 结构](../../winscript/reference/profiler-heap-object-structure.md)结构和与其相关联[PROFILER_HEAP_OBJECT_OPTIONAL_INFO 结构](../../winscript/reference/profiler-heap-object-optional-info-structure.md)元素。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT FreeObjectAndOptionalInfo (    [in] ULONG celt,    [in, size_is(celt)] PROFILER_HEAP_OBJECT** heapObjects);  
```  
  
#### <a name="parameters"></a>参数  
 `celt`  
 要释放的对象数。  
  
 `heapObjects`  
 数组[PROFILER_HEAP_OBJECT 结构](../../winscript/reference/profiler-heap-object-structure.md)结构。  
  
## <a name="return-value"></a>返回值  
 HRESULT。