---
title: "IDebugDocumentHost::GetDeferredText |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHost.GetDeferredText
apilocation: scrobj.dll
helpviewer_keywords: IDebugDocumentHost::GetDeferredText
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ace3bdbfef143a3307d81455788a1e81788cb50b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
返回添加的使用的字符范围`IDebugDocumentHelper::AddDeferredText`中原始主机文档的方法。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetDeferredText(  
   DWORD              dwTextStartCookie,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>参数  
 `dwTextStartCookie`  
 [in]表示文本的起始位置的主机定义的 cookie。  
  
 `pcharText`  
 [在中，out]字符文本缓冲区。 如果此参数，此方法不返回字符`NULL`。  
  
 `pstaTextAttr`  
 [在中，out]字符属性缓冲区。 如果此参数，此方法不返回属性`NULL`。  
  
 `pcNumChars`  
 [在中，out]指示返回的字符/属性的实际数目。 此参数必须设置为零之前调用此方法。  
  
 `cMaxChars`  
 [in]要返回的字符最大数量。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_NOTIMPL`|未实现方法。|  
  
## <a name="remarks"></a>备注  
 此方法可能返回`E_NOTIMPL`，如果主机不会调用`IDebugDocumentHelper::AddDeferredText`。  
  
> [!NOTE]
>  此方法返回从原始文档的文本。 主机不跟踪的编辑或对文档的其他更改。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugDocumentHost 接口](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [SOURCE_TEXT_ATTR 枚举](../../winscript/reference/source-text-attr-enumeration.md)