---
title: "IDebugExpression::QueryIsComplete |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugExpression.QueryIsComplete
apilocation: jscript.dll
helpviewer_keywords: IDebugExpression::QueryIsComplete
ms.assetid: 510d62e5-a316-46fb-b23f-d3ba902b295c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c1d72b2a2d41b748954f2e4b2b4aa9f0011ca670
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressionqueryiscomplete"></a>IDebugExpression::QueryIsComplete
确定操作是否完成。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT QueryIsComplete();  
```  
  
#### <a name="parameters"></a>参数  
 此方法采用任何参数。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功，并在操作未完成。|  
|`S_FALSE`|操作仍处于挂起状态。|  
  
## <a name="remarks"></a>备注  
 此方法可确定操作是否完成。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugExpression 接口](../../winscript/reference/idebugexpression-interface.md)