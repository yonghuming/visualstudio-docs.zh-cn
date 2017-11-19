---
title: "IRemoteDebugApplicationEvents::OnDisconnectDebugger |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplicationEvents.OnDisconnectDebugger
apilocation: jscript.dll
helpviewer_keywords: IRemoteDebugApplicationEvents::OnDisconnectDebugger
ms.assetid: ea11cde0-1484-4181-a5dd-a1f6cf788892
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 014da34fb9f7c6f3841d44a354320ff55bacc316
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationeventsondisconnectdebugger"></a>IRemoteDebugApplicationEvents::OnDisconnectDebugger
调试器处理断开连接事件。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT OnDisconnectDebugger();  
```  
  
#### <a name="parameters"></a>参数  
 此方法采用任何参数。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法可处理调试器断开连接事件。  
  
## <a name="see-also"></a>另请参阅  
 [IRemoteDebugApplicationEvents 接口](../../winscript/reference/iremotedebugapplicationevents-interface.md)