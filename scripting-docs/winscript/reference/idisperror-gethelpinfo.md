---
title: "IDispError::GetHelpInfo |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispError.GetHelpInfo
apilocation: scrobj.dll
helpviewer_keywords: IDispError::GetHelpInfo
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17098b4055bb61e9a2f639404edfe2214abc931e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
返回的帮助文件的路径和解释该错误，如有可能的主题的上下文 ID。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pbstrFileName`  
 [out]包含帮助文件的完全限定的路径的字符串。 如果没有帮助文件，或发生错误，则返回值为 NULL。  
  
 `pdwContext`  
 [out]错误帮助上下文 ID。 如果没有帮助文件 (如果`pbstrFileName`为 NULL)，此参数没有任何意义。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|发生了特定于提供程序错误。|  
|`E_INVALIDARG`|`pbstrFileName`或`pdwContext`为 null。|  
|`E_OUTOFMEMORY`|提供程序无法分配足够的内存中要返回的帮助文件路径。|  
  
## <a name="remarks"></a>备注  
 此方法返回的帮助文件的路径和解释该错误，如有可能的主题的上下文 ID。  
  
> [!NOTE]
>  未实现此方法。  
  
## <a name="see-also"></a>另请参阅  
 [IDispError 接口](../../winscript/reference/idisperror-interface.md)