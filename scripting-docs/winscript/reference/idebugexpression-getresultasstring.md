---
title: "IDebugExpression::GetResultAsString |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugExpression.GetResultAsString
apilocation: jscript.dll
helpviewer_keywords: IDebugExpression::GetResultAsString
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 557fe65859d1e3046d64884982070ad233e12559
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressiongetresultasstring"></a>IDebugExpression::GetResultAsString
返回一个字符串，以及操作的返回值的表达式计算的结果。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### <a name="parameters"></a>参数  
 `phrResult`  
 [out]操作的返回值。  
  
 `pbstrResult`  
 [out]表达式的计算结果。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_PENDING`|操作仍处于挂起状态。|  
  
## <a name="remarks"></a>备注  
 此方法返回的结果作为字符串，该操作的表达式计算`HRESULT`。  
  
 此方法返回`S_OK`和`phrResult`返回`E_ABORT`如果`Abort`将中止此操作。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugExpression 接口](../../winscript/reference/idebugexpression-interface.md)