---
title: "IDebugCodeContext::SetBreakPoint |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugCodeContext.SetBreakPoint
apilocation: jscript.dll
helpviewer_keywords: IDebugCodeContext::SetBreakPoint
ms.assetid: ecd42eae-66fa-40d3-9e47-08b826784108
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a0111deba23f29aa6b7d31a1aed8d729ff4e7fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugcodecontextsetbreakpoint"></a>IDebugCodeContext::SetBreakPoint
设置或清除在此代码上下文断点。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT SetBreakPoint(  
   BREAKPOINT_STATE  bps  
);  
```  
  
#### <a name="parameters"></a>参数  
 `bps`  
 [in]指定此代码上下文的断点状态。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法设置，或清除在此代码上下文断点。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugCodeContext 接口](../../winscript/reference/idebugcodecontext-interface.md)   
 [BREAKPOINT_STATE 枚举](../../winscript/reference/breakpoint-state-enumeration.md)