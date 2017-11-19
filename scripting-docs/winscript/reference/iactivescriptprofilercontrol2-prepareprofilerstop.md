---
title: "IActiveScriptProfilerControl2::PrepareProfilerStop |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptProfilerControl2::PrepareProfilerStop
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78078cd874be1d7d3d169be2d3d70e65866be3fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
通知探查器将停止所有适用的脚本引擎上进行分析。 通过使用此方法，你可以获取完整的调用堆栈，如果[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]时停止分析运行。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT PrepareProfilerStop();  
```  
  
#### <a name="parameters"></a>参数  
 方法不接受任何参数。  
  
## <a name="return-value"></a>返回值  
 返回一个 HRESULT。 可能的值如下：  
  
|返回值|含义|  
|------------------|-------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|无法启动分析。|  
|`S_FALSE`|未运行脚本时，已停止分析。|  
|`ACTIVPROF_E_PROFILER_ABSENT`|未启用分析。|  
  
## <a name="remarks"></a>备注  
 调用`IActiveScriptProfilerControl2::PrepareProfilerStop`可确保将发送事件调用堆栈中的函数。 此方法必须在调用之前停止任何当前选项卡上的脚本引擎上进行分析。可以针对任何脚本引擎调用方法。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [IActiveScriptProfilerControl2 接口](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)