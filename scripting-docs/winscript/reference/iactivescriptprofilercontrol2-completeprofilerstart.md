---
title: "IActiveScriptProfilerControl2::CompleteProfilerStart |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptProfilerControl2::CompleteProfilerStart
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5abd4ee4237991714bfe3d8ba21b083f1a1920cd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
通知探查器已启动所有适用的脚本引擎上进行分析。 通过使用此方法，你可以获取完整的调用堆栈，如果[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]开始分析时处于运行状态。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>参数  
 方法不接受任何参数。  
  
## <a name="return-value"></a>返回值  
 返回一个 HRESULT。 可能的值如下：  
  
|返回值|含义|  
|------------------|-------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|无法启动分析。|  
|`S_FALSE`|未运行脚本时，分析已启动。|  
|`ACTIVPROF_E_PROFILER_ABSENT`|未启用分析。 不执行回调的设置。|  
|`E_OUTOFMEMORY`|调用堆栈无法获得由于内存不足情况。|  
  
## <a name="remarks"></a>备注  
 调用`IActiveScriptProfilerControl2::CompleteProfilerStart`可确保将发送事件已在调用堆栈的函数。 此方法具有分析上的当前选项卡上任何脚本引擎启动后调用。可以针对任何脚本引擎调用方法。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [IActiveScriptProfilerControl2 接口](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)