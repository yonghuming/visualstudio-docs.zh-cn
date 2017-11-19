---
title: "IDebugAsyncOperation::GetResult |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugAsyncOperation.GetResult
apilocation: pdm.dll
helpviewer_keywords: IDebugAsyncOperation::GetResult
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60181904408010f35fa4d99d182216e665583aab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
提供的返回值和从同步调试操作返回的对象参数。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>参数  
 `phrResult`  
 [out]如果该操作已完成，`phrResult`是返回值的`IDebugSyncOperation::Execute`。  
  
 `ppunkResult`  
 [out]如果该操作已完成，`ppunkResult`是操作返回的对象参数。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_PENDING`|未完成该操作。|  
  
## <a name="remarks"></a>备注  
 如果该操作已完成，此方法返回`HRESULT`和对象参数从`IDebugSyncOperation::Execute`。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugAsyncOperation 接口](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)