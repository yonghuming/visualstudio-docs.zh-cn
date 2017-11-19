---
title: "IActiveScriptAuthor::GetChars |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.GetChars
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::GetChars
ms.assetid: a73ba263-12f7-4d5f-b4c8-9ad7e2d5d3cb
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: abc9c819c2dd4a75d6223af86b4fe89baebc186b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetchars"></a>IActiveScriptAuthor::GetChars
返回的请求的完成上下文的完成字符集。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### <a name="parameters"></a>参数  
 `fRequestedList`  
 [in]请求的完成上下文中。  
  
|常量|值|描述|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|从 0x0001|请求左侧枚举。|  
|SCRIPT_CMPL_MEMBER_TRIGGER|0x0002|请求的成员完成上下文。|  
|SCRIPT_CMPL_PARAM_TRIGGER|0x0003|请求的参数列表。|  
|SCRIPT_CMPL_COMMIT|0x0004|参数列表的请求完成。|  
  
 `pbstrChars`  
 [out]对应于请求的完成上下文字符。  
  
|`fRequestedList`参数|返回字符|  
|--------------------------------|-------------------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|"."|  
|SCRIPT_CMPL_MEMBER_TRIGGER|"="|  
|SCRIPT_CMPL_PARAM_TRIGGER|"(,"|  
|SCRIPT_CMPL_COMMIT|"()"|  
  
## <a name="return-value"></a>返回值  
 一个 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptAuthor 接口](../../winscript/reference/iactivescriptauthor-interface.md)