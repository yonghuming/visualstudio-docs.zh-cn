---
title: "IDispError::GetHresult |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispError.GetHresult
apilocation: scrobj.dll
helpviewer_keywords: IDispError::GetHresult
ms.assetid: a14d566e-473f-497b-a2f9-85331433e6c9
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 859708b8aec4f89dd1ea49bf6e248d7bcade7624
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idisperrorgethresult"></a>IDispError::GetHresult
检索中的错误代码`IDispError`对象。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetHresult(  
   HRESULT*  phr  
);  
```  
  
#### <a name="parameters"></a>参数  
 `phr`  
 [out]指定的错误代码。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法检索中的错误代码`IDispError`对象。  
  
> [!NOTE]
>  未实现此方法。  
  
## <a name="see-also"></a>另请参阅  
 [IDispError 接口](../../winscript/reference/idisperror-interface.md)