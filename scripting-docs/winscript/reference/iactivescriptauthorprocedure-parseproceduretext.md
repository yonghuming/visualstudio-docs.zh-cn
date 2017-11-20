---
title: "IActiveScriptAuthorProcedure::ParseProcedureText |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthorProcedure.ParseProcedureText
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthorProcedure::ParseProcedureText
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9c4a1ba03a8498dbaa857dc5dbabba8914e54a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
分析代码过程，将代码过程的文本添加到创作引擎，该脚本并创建`IScriptEntry`对应于代码过程的对象。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pszCode`  
 [in]要分析的脚本文本。  
  
 `pszFormalParams`  
 [in]该过程的形式参数名称的地址。 必须按创作引擎脚本适当的分隔符分隔的参数名称。 名称不应括在括号中。  
  
 `pszProcedureName`  
 [in]要分析的过程名称的地址。  
  
 `pszItemName`  
 [in]包含的项名称的缓冲区地址与`IScriptEntry`对象。  
  
 `pszDelimiter`  
 [in]结束的脚本块分隔符的地址。 当`pszCode`分析从文本流中，主机通常使用分隔符 （如两个单引号），来检测脚本块的末尾。 如果没有定界符来标记该脚本块的末尾，此参数设置为 NULL。  
  
 `dwCookie`  
 [in]应用程序定义的值与新的`IScriptEntry`对象。  
  
 `dwFlags`  
 [in]未使用。  
  
 `pdispFor`  
 [in]未使用。  
  
## <a name="return-value"></a>返回值  
 一个 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 当前[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]引擎未实现此方法。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptAuthorProcedure 接口](../../winscript/reference/iactivescriptauthorprocedure-interface.md)