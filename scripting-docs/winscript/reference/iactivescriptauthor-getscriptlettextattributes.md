---
title: "IActiveScriptAuthor::GetScriptletTextAttributes |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.GetScriptletTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::GetScriptletTextAttributes
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b01fba7d0e8eb80fed51b1ff0ebd3a8816bacb01
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
返回 scriptlet 的文本属性。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR pszCode,  
   ULONG cch,  
   LPCOLESTR pszDelimiter,  
   DWORD dwFlags,  
   SOURCE_TEXT_ATTR *pattr  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pszCode`  
 [在 size_is (`cch`)] 的 scriptlet 文本。 此字符串没有要终止 null。  
  
 `cch`  
 [in]用于的大小`pszCode`和`pattr`参数。  
  
 `pszDelimiter`  
 [in]最终的 scriptlet 分隔符的地址。 当`pszCode`分析从文本流中，主机通常使用分隔符 （如两个单引号），来检测 scriptlet 的末尾。 如果无分隔符用于确定 scriptlet 的结尾，此参数设置为 NULL。  
  
 `dwFlags`  
 [in]与 scriptlet 文本特性关联的标志。 可以是以下值的组合。  
  
|常量|值|描述|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|从 0x0001|确定具有 SOURCETEXT_ATTR_IDENTIFIER 属性的标识符，并标识圆点运算符具有 SOURCETEXT_ATTR_MEMBERLOOKUP 属性。|  
|GETATTRFLAG_THIS|0x0100|标识具有 SOURCETEXT_ATTR_THIS 属性的当前对象。|  
|GETATTRFLAG_HUMANTEXT|0x8000|标识具有 SOURCETEXT_ATTR_HUMANTEXT 特性的字符串内容和注释文本。|  
  
 `pattr`  
 [传入、 传出 size_is (`cch`)] scriptlet 代码的颜色信息。  
  
## <a name="return-value"></a>返回值  
 一个 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptAuthor 接口](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [SOURCE_TEXT_ATTR 枚举](../../winscript/reference/source-text-attr-enumeration.md)