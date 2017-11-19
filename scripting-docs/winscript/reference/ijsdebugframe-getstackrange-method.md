---
title: "Ijsdebugframe:: Getstackrange 方法 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugFrame.GetStackRange
apilocation: jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cce4d4542f4f76657475636ad6d8e430e1909181
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugframegetstackrange-method"></a>IJsDebugFrame::GetStackRange 方法
返回逻辑的 JavaScript 堆栈帧的绝对地址范围。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pStart`  
 [out]下帧的大多数堆栈的指针。  
  
 `pEnd`  
 [out]最高帧的大多数集纸器的指针。  
  
## <a name="return-value"></a>返回值  
  
## <a name="remarks"></a>备注  
 此方法可用于从多个运行时收集的交错的堆栈跟踪进行汇总。 开始时，最终堆栈指针可以包含多个物理计算机堆栈帧 （对于解释型 JavaScript 运行时帧）。 启动 > 结束随着堆栈从高到低的地址。  
  
## <a name="requirements"></a>要求  
 **标头：** jscript9diag.h  
  
## <a name="see-also"></a>另请参阅  
 [IJsDebugFrame 接口](../../winscript/reference/ijsdebugframe-interface.md)