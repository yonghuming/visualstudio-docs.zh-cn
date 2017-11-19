---
title: "IEnumRemoteDebugApplications::Clone |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumRemoteDebugApplications.Clone
apilocation: scrobj.dll
helpviewer_keywords: IEnumRemoteDebugApplications::Clone
ms.assetid: 762f6dac-1be4-49ec-afda-68c1b29f7a4b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97b135d0139be40fa864064422027e7c3247fc8a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ienumremotedebugapplicationsclone"></a>IEnumRemoteDebugApplications::Clone
创建一个枚举器，其中包含与当前的枚举器相同的状态。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT Clone(  
   IEnumRemoteDebugApplications**  ppessd  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ppessd`  
 [out]枚举器的克隆。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法创建一个枚举器，其中包含与当前的枚举器相同的状态。  
  
## <a name="see-also"></a>另请参阅  
 [IEnumRemoteDebugApplications 接口](../../winscript/reference/ienumremotedebugapplications-interface.md)