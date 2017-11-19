---
title: "IApplicationDebugger::QueryAlive |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IApplicationDebugger.QueryAlive
apilocation: scrobj.dll
helpviewer_keywords: IApplicationDebugger::QueryAlive
ms.assetid: 41181ebb-a3bf-4e41-82af-d6c7348dc706
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48571476407c29b9af949bd6f626d14ea822f2e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggerqueryalive"></a>IApplicationDebugger::QueryAlive
指示调试器是否处于响应状态。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT QueryAlive();  
```  
  
#### <a name="parameters"></a>参数  
 此方法采用任何参数。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法指示调试器是否响应。 此方法的实现应始终返回`S_OK`。  
  
 如果调试器进程意外终止，COM 从用于调用此方法的封送处理代理返回错误。  
  
## <a name="see-also"></a>另请参阅  
 [IApplicationDebugger 接口](../../winscript/reference/iapplicationdebugger-interface.md)