---
title: "IActiveScriptProfilerCallback::Shutdown |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerCallback.Shutdown
apilocation: scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec47cd5f581c36abb60b662983c6d806a4732f47
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallbackshutdown"></a>IActiveScriptProfilerCallback::Shutdown
调用以通知探查器对象，每当分析脚本引擎已停止。 这样一来，如果需要，探查器对象可以调用其清理例程。 当脚本引擎正在关闭，或者当对的调用还通过脚本引擎调用此方法[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)失败。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### <a name="parameters"></a>参数  
 `hrReason`  
 [in]有关关闭原因。 如果脚本引擎正在关闭，`S_OK`被传递。 如果调用[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)返回失败 HRESULT，HRESULT 被传递。 否则，此值从检索[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)。  
  
## <a name="return-value"></a>返回值  
 通过脚本引擎忽略此方法的返回值。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptProfilerCallback 接口](../../winscript/reference/iactivescriptprofilercallback-interface.md)