---
title: "IEnumDebugStackFrames::Clone |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumDebugStackFrames.Clone
apilocation: jscript.dll
helpviewer_keywords: IEnumDebugStackFrames::Clone
ms.assetid: 9d9e01a3-0be3-4336-832a-f065af388571
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 910b05024efcde8614882e0c95cdfab2ffe9be3e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugstackframesclone"></a>IEnumDebugStackFrames::Clone
创建一个枚举器，其中包含与当前的枚举器相同的状态。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT Clone(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ppedsf`  
 [out]返回`IEnumDebugStackFrames`接口的枚举器的克隆。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法创建一个枚举器，其中包含与当前的枚举器相同的状态。  
  
## <a name="see-also"></a>另请参阅  
 [IEnumDebugStackFrames 接口](../../winscript/reference/ienumdebugstackframes-interface.md)