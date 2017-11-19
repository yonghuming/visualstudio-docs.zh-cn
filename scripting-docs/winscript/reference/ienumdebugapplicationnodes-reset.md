---
title: "IEnumDebugApplicationNodes::Reset |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumDebugApplicationNodes.Reset
apilocation: pdm.dll
helpviewer_keywords: IEnumDebugApplicationNodes::Reset
ms.assetid: 56ecdafe-ff11-461a-92e1-93254a49f1a1
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b237117a942beb3564d8b5012231aca1df1c4ad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugapplicationnodesreset"></a>IEnumDebugApplicationNodes::Reset
将枚举序列重置到开头。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT Reset();  
```  
  
#### <a name="parameters"></a>参数  
 此方法采用任何参数。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法将枚举序列重置到开头。  
  
## <a name="see-also"></a>另请参阅  
 [IEnumDebugApplicationNodes 接口](../../winscript/reference/ienumdebugapplicationnodes-interface.md)