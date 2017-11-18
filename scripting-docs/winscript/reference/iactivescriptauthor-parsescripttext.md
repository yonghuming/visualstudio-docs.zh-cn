---
title: "IActiveScriptAuthor::ParseScriptText |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.ParseScriptText
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::ParseScriptText
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 13e81d96ae817b2117f12cb56fd59759f4c2b849
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
分析脚本文本，将文本添加到创作引擎，该脚本并创建`IScriptEntry`对应于脚本块的对象。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT ParseScriptText(  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pszCode`  
 [in]要分析的脚本文本。  
  
 `pszItemName`  
 [in]包含与脚本块关联的项名称的缓冲区地址。  
  
 `pszDelimiter`  
 [in]结束的脚本块分隔符的地址。 当`pszCode`分析从文本流中，主机通常使用分隔符 （如两个单引号），来检测脚本块的末尾。 如果没有定界符来确定该脚本块的结尾，此参数设置为 NULL。  
  
 `dwCookie`  
 [in]应用程序定义的值与新的`IScriptEntry`对象。  
  
 `dwFlags`  
 [in]未使用。  
  
## <a name="return-value"></a>返回值  
 一个 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptAuthor 接口](../../winscript/reference/iactivescriptauthor-interface.md)