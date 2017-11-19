---
title: "IDebugAsyncOperation::QueryIsComplete |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugAsyncOperation.QueryIsComplete
apilocation: pdm.dll
helpviewer_keywords: IDebugAsyncOperation::QueryIsComplete
ms.assetid: fcf6e229-4d40-46d9-ab81-d3561bc8e084
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e985697e425ec4966f2260792a9698fa50b4c98d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperationqueryiscomplete"></a>IDebugAsyncOperation::QueryIsComplete
确定是否已完成调试操作。  
  
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
|`S_OK`|操作已完成。|  
|`S_FALSE`|该操作不完整。|  
  
## <a name="remarks"></a>备注  
 此方法可确定是否已完成调试操作。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugAsyncOperation 接口](../../winscript/reference/idebugasyncoperation-interface.md)