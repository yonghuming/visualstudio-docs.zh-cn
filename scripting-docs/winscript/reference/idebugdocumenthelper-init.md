---
title: "IDebugDocumentHelper::Init |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.Init
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::Init
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 45cd57e4ba9e86bf84f927f487c637d61aa5339b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
`Init`方法初始化具有名称和初始的属性的调试文档帮助。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pda`  
 [in]调试应用程序与此文档关联。  
  
 `pszShortName`  
 [in]以 null 结尾的字符串，包含文档的短名称。  
  
 `pszLongName`  
 [in]以 null 结尾的字符串，包含长名称的文档。  
  
 `docAttr`  
 [in]指定文本文档属性。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法初始化具有名称和初始的属性的调试文档帮助。  
  
 本文档不会显示在树中，直到`IDebugDocumentHelper::Attach`调用。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [IDebugDocumentHelper 接口](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [TEXT_DOC_ATTR 常量](../../winscript/reference/text-doc-attr-constants.md)