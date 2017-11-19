---
title: "IDebugExpression::GetResultAsDebugProperty |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugExpression.GetResultAsDebugProperty
apilocation: jscript.dll
helpviewer_keywords: IDebugExpression::GetResultAsDebugProperty
ms.assetid: 9075bf2f-d5bb-464e-b6c2-3fa3215e9ae0
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6ce67df5dd55bd8c1ae55bb19fe2a19aed9e40f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressiongetresultasdebugproperty"></a>IDebugExpression::GetResultAsDebugProperty
返回为调试属性和操作的返回值的表达式计算的结果。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetResultAsDebugProperty(  
   HRESULT*          phrResult,  
   IDebugProperty**  ppdp  
);  
```  
  
#### <a name="parameters"></a>参数  
 `phrResult`  
 [out]操作的返回值。  
  
 `ppdp`  
 [out]表达式调试属性。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_PENDING`|操作仍处于挂起状态。|  
  
## <a name="remarks"></a>备注  
 此方法返回作为表达式计算的结果`IDebugProperty`和操作的`HRESULT`。  
  
 此方法返回`S_OK`和`phrResult`返回`E_ABORT`如果`Abort`将中止此操作。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugExpression 接口](../../winscript/reference/idebugexpression-interface.md)   
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)