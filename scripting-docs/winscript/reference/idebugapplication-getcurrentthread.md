---
title: "IDebugApplication::GetCurrentThread |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.GetCurrentThread
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::GetCurrentThread
ms.assetid: 15128e77-6fc6-42a2-8c04-20e22ef03f29
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2240a62b62c917e94f3ace8f516a10f9de66c74d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationgetcurrentthread"></a>IDebugApplication::GetCurrentThread
返回与当前正在运行的线程关联的线程。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetCurrentThread(  
   IDebugApplicationThread**  pat  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pat`  
 [out]与当前正在运行的线程相关的线程。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法返回与当前正在运行的线程关联的线程。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugApplication 接口](../../winscript/reference/idebugapplication-interface.md)