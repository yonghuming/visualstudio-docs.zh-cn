---
title: "IActiveScriptProfilerCallback::FunctionCompiled |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerCallback.FunctionCompiled
apilocation: scrobj.dll
ms.assetid: a7e9ef17-3891-4731-9d08-c37bc489be61
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 797476d4892224ad0b27c9caf579c0704693c835
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
通知探查器对象的脚本引擎编译脚本时遇到一个函数。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>参数  
 `functionId`  
 [in]函数的唯一 ID。 通过脚本引擎分配有此 ID。  
  
 `scriptId`  
 [in]该脚本中函数的唯一 ID。  
  
 `pwszFunctionName`  
 [in]匿名函数的函数或为 null 的名称。  
  
 `pwszFunctionNameHint`  
 [in]函数或如果脚本引擎不推断任何名称则为 null 的推断的名称。  
  
 `pIDebugDocumentContext`  
 [in]如果可用，将指针与`IUnknown`探查器必须查询的接口[IDebugDocumentContext 接口](../../winscript/reference/idebugdocumentcontext-interface.md)指针。 否则为 null。  
  
## <a name="return-value"></a>返回值  
 通过脚本引擎忽略此方法的返回值。  
  
## <a name="remarks"></a>备注  
 仅当主机支持此功能，脚本引擎可以提供的文档上下文。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptProfilerCallback 接口](../../winscript/reference/iactivescriptprofilercallback-interface.md)