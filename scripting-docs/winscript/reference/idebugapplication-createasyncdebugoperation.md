---
title: "IDebugApplication::CreateAsyncDebugOperation |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.CreateAsyncDebugOperation
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::CreateAsyncDebugOperation
ms.assetid: bc32b101-6364-4498-8458-bd5f3ab5ad94
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8714f4401249d73cf09d241ebf4c2b2115911d6b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationcreateasyncdebugoperation"></a>IDebugApplication::CreateAsyncDebugOperation
提供对给定同步调试操作的异步访问。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT CreateAsyncDebugOperation(  
   IDebugSyncOperation*    psdo,  
   IDebugAsyncOperation**  ppado  
);  
```  
  
#### <a name="parameters"></a>参数  
 `psdo`  
 [in]同步调试操作对象。  
  
 `ppado`  
 [out]异步调试操作对象。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法允许语言引擎来以异步方式计算表达式，但未显式与调试器线程同步。 有关详细信息，请参阅[IDebugSyncOperation 接口](../../winscript/reference/idebugsyncoperation-interface.md)和[IDebugAsyncOperation 接口](../../winscript/reference/idebugasyncoperation-interface.md)。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugApplication 接口](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugSyncOperation 接口](../../winscript/reference/idebugsyncoperation-interface.md)   
 [IDebugAsyncOperation 接口](../../winscript/reference/idebugasyncoperation-interface.md)