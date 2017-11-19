---
title: "IRemoteDebugApplication::DisconnectDebugger |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplication.DisconnectDebugger
apilocation: pdm.dll
helpviewer_keywords: IRemoteDebugApplication::DisconnectDebugger
ms.assetid: 989e5a34-0267-4a2e-96b6-e1dcc2ffe883
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: facbe73a404ace07ad91e403a26e94008d0a3e67
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationdisconnectdebugger"></a>IRemoteDebugApplication::DisconnectDebugger
断开当前的调试器与应用程序的连接。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT DisconnectDebugger();  
```  
  
#### <a name="parameters"></a>参数  
 此方法采用任何参数。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法在应用程序中断开当前的调试器。  
  
## <a name="see-also"></a>另请参阅  
 [IRemoteDebugApplication 接口](../../winscript/reference/iremotedebugapplication-interface.md)