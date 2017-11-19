---
title: "IDebugStackFrame::GetCodeContext |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugStackFrame.GetCodeContext
apilocation: jscript.dll
helpviewer_keywords: IDebugStackFrame::GetCodeContext
ms.assetid: 3dd378f3-e4b7-413e-8812-0f6c72952544
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b872e63169f6c2d70cd3476324b3d0071718350
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframegetcodecontext"></a>IDebugStackFrame::GetCodeContext
返回与此堆栈帧关联的当前代码上下文。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetCodeContext(  
   IDebugCodeContext**  ppcc  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ppcc`  
 [out]与此堆栈帧关联的代码上下文。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法返回与此堆栈帧关联的当前代码上下文。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugStackFrame 接口](../../winscript/reference/idebugstackframe-interface.md)