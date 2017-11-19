---
title: "IActiveScriptProfilerCallback2::OnFunctionEnterByName |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptProfilerCallback2::OnFunctionEnterByName
ms.assetid: 24b1593a-97fc-4d70-9b85-ec86fb59f987
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea74d9e9e00485c86d26bb01c486992f85ffeb8f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallback2onfunctionenterbyname"></a>IActiveScriptProfilerCallback2::OnFunctionEnterByName
通知脚本引擎将执行文档对象模型 (DOM) 函数调用的探查器对象。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### <a name="parameters"></a>参数  
 `pwszFunctionName`  
 [in]脚本引擎将执行的函数名称。  
  
 `scriptType`  
 [in]函数的类型。 有关有效值的说明，请参阅[PROFILER_SCRIPT_TYPE 枚举](../../winscript/reference/profiler-script-type-enumeration.md)。  
  
## <a name="return-value"></a>返回值  
 通过脚本引擎忽略此方法的返回值。  
  
## <a name="remarks"></a>备注  
 对于 DOM 调用，脚本引擎调用此方法而不是调用[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)。 这是由于大量的唯一方法和属性的数组。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)   
 [IActiveScriptProfilerCallback2 接口](../../winscript/reference/iactivescriptprofilercallback2-interface.md)