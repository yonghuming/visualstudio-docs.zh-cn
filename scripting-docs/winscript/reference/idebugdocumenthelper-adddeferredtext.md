---
title: "IDebugDocumentHelper::AddDeferredText |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.AddDeferredText
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::AddDeferredText
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c92909874429075bebc6a1f0a252573d049584e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
给定的文本可用，但它不提供字符，则通知帮助器。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>参数  
 `cChars`  
 [in]若要添加的 (Unicode) 字符数。  
  
 `dwTextStartCookie`  
 [in]表示文本的起始位置的主机定义的 cookie。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|方法失败。|  
  
## <a name="remarks"></a>备注  
 此方法允许宿主延迟提供要添加，直到需要它们，同时允许帮助器以生成准确的通知和大小信息的字符。 `dwTextStartCookie`参数是一个 cookie，由宿主，后者表示文本的起始位置。 后续调用`IDebugDocumentText::GetText`必须提供此 cookie。 例如，在主机上表示在 DBCS 中的文本，cookie 可能的字节偏移量。  
  
 它假定进行单个调用`IDebugDocumentText::GetText`可以从多个调用中获取字符`AddDeferredText`。 帮助器类可能还要求具有相同范围的延迟字符不止一次。  
  
> [!NOTE]
>  调用`AddDeferredText`不应通过调用混合`AddUnicodeText`或`AddDBCSText`。 如果发生这种情况，`E_FAIL`返回。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugDocumentHelper 接口](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)