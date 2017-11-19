---
title: "IDebugDocumentInfo::GetName |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentInfo.GetName
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentInfo::GetName
ms.assetid: c25d73da-99b6-4c9f-82af-182b4853f81c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da369c328c2f92915c60b1c50517938bf76d5202
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentinfogetname"></a>IDebugDocumentInfo::GetName
返回指定的文档名称。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### <a name="parameters"></a>参数  
 `dnt`  
 [in]要返回的文档名称的类型。  
  
 `pbstrName`  
 [out]包含名称的字符串。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|指定的文档名称未知。|  
  
## <a name="remarks"></a>备注  
 此方法返回指定的文档名称。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugDocumentInfo 接口](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [DOCUMENTNAMETYPE 枚举](../../winscript/reference/documentnametype-enumeration.md)