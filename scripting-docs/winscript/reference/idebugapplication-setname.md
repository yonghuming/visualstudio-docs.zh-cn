---
title: "IDebugApplication::SetName |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.SetName
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::SetName
ms.assetid: 7b0ddc58-6f20-4ce3-9bdf-81a6c1d64256
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad54c1c9ba950c7f1b98d393bec2bf65c385ec60
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationsetname"></a>IDebugApplication::SetName
设置应用程序的名称。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT SetName(  
   LPCOLESTR  pstrName  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pstrName`  
 [in]应用程序的名称。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 提供给此方法的名称在后续调用中返回`IRemoteDebugApplication::GetName`方法。  
  
 应该在调用之前调用此方法`IProcessDebugManager::AddApplication`方法。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugApplication 接口](../../winscript/reference/idebugapplication-interface.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)