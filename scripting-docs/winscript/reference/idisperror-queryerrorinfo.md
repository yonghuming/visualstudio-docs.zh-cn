---
title: "IDispError::QueryErrorInfo |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispError.QueryErrorInfo
apilocation: scrobj.dll
helpviewer_keywords: IDispError::QueryErrorInfo
ms.assetid: e7e71a14-77e2-4331-9ffc-1dace041fa84
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a165edf2d8f9a0b386daa0035ece1a722401a443
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idisperrorqueryerrorinfo"></a>IDispError::QueryErrorInfo
检索特定类型的错误信息。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT QueryErrorInfo(  
   GUID  guidErrorType,  
   IDispError**  ppde  
);  
```  
  
#### <a name="parameters"></a>参数  
 `guidErrorType`  
 [in]指定错误类型的 GUID。  
  
 `ppde`  
 [out]指定的 IDispError 对象。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 `QueryErrorInfo`方法检索特定类型的错误信息。  
  
> [!NOTE]
>  未实现此方法。  
  
## <a name="see-also"></a>另请参阅  
 [IDispError 接口](../../winscript/reference/idisperror-interface.md)