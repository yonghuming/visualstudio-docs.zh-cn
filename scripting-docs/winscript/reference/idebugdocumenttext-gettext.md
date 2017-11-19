---
title: "IDebugDocumentText::GetText |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentText.GetText
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentText::GetText
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a1006304974fab4959ad6313ffdc26793cdd345
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
检索字符和/或与字符位置范围关联的字符属性。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetText(  
   ULONG              cCharacterPosition,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>参数  
 `cCharacterPosition`  
 [in]启动范围内的字符位置的位置。  
  
 `pcharText`  
 [在中，out]字符文本缓冲区。 缓冲区必须大到足以保留`cMaxChars`字符。 如果此参数为 NULL，则该方法不返回字符。  
  
 `pstaTextAttr`  
 [在中，out]字符属性缓冲区。 缓冲区必须大到足以保留`cMaxChars`字符。 如果此参数为 NULL，则该方法不返回属性。  
  
 `pcNumChars`  
 [在中，out]返回字符/属性数。 此参数必须设置为零之前调用此方法。  
  
 `cMaxChars`  
 [in]字符位置范围中的字符数。 此外指定要返回字符最大的数量。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法检索字符和/或与字符位置范围关联的字符属性。 字符位置范围被指定字符位置和的字符数。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugDocumentText 接口](../../winscript/reference/idebugdocumenttext-interface.md)   
 [SOURCE_TEXT_ATTR 枚举](../../winscript/reference/source-text-attr-enumeration.md)