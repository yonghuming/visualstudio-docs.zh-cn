---
title: "IRemoteDebugApplicationEvents::OnDestroyThread |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplicationEvents.OnDestroyThread
apilocation: jscript.dll
helpviewer_keywords: IRemoteDebugApplicationEvents::OnDestroyThread
ms.assetid: 7c716ccc-7b82-41b2-9a16-d0366999dee8
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af2d671a6c93cde39c2e3e644243d666e1cd5d46
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationeventsondestroythread"></a>IRemoteDebugApplicationEvents::OnDestroyThread
处理线程销毁事件。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT OnDestroyThread(  
   IRemoteDebugApplicationThread*  prdat  
);  
```  
  
#### <a name="parameters"></a>参数  
 `prdat`  
 [in]已被销毁线程。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法可处理线程销毁事件。  
  
## <a name="see-also"></a>另请参阅  
 [IRemoteDebugApplicationEvents 接口](../../winscript/reference/iremotedebugapplicationevents-interface.md)