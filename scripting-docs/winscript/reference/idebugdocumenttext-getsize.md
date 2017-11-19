---
title: "IDebugDocumentText::GetSize |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentText.GetSize
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentText::GetSize
ms.assetid: 9da53856-613a-44b2-a84c-99454a2a1548
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3152150c46793a71ec7a46b6ab2097efa06f6fc8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextgetsize"></a>IDebugDocumentText::GetSize
返回文档中的行数和字符数。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetSize(  
   ULONG*  pcNumLines,  
   ULONG*  pcNumChars  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pcNumLines`  
 [out]在文档中的行数。 如果此参数为 NULL，则该方法不返回值。  
  
 `pcNumChars`  
 [out]在文档中的字符数。 如果此参数为 NULL，则该方法不返回值。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法返回文档中的行数和字符数。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugDocumentText 接口](../../winscript/reference/idebugdocumenttext-interface.md)