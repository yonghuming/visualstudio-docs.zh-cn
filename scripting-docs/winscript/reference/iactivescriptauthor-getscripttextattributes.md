---
title: "IActiveScriptAuthor::GetScriptTextAttributes |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.GetScriptTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::GetScriptTextAttributes
ms.assetid: a53451de-cc5c-4b53-8e5f-81e196364caf
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aa96623b4356f0a3d17c8b2631840953dac2d51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetscripttextattributes"></a>IActiveScriptAuthor::GetScriptTextAttributes
返回一个脚本块的文本属性。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetScriptTextAttributes(  
    LPCOLESTR        pszCode,  
    ULONG            cch,  
    LPCOLESTR        pszDelimiter,  
    DWORD            dwFlags,  
    SOURCE_TEXT_ATTR *pattr);  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pszCode`  
 [在 size_is (`cch`)] 的脚本块的文本。 此字符串没有要终止 null。  
  
 `cch`  
 [in]用于的大小`pszCode`和`pattr`参数。  
  
 `pszDelimiter`  
 [in]结束脚本分隔符的地址。 当`pszCode`分析从文本流中，主机通常使用分隔符 （如两个单引号），来检测 scriptlet 的末尾。 如果没有定界符来确定该脚本块的结尾，此参数设置为 NULL。  
  
 `dwFlags`  
 [in]与脚本块文本特性关联的标志。 可以是以下值的组合：  
  
|常量|值|描述|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|从 0x0001|确定具有 SOURCETEXT_ATTR_IDENTIFIER 属性的标识符，并标识圆点运算符具有 SOURCETEXT_ATTR_MEMBERLOOKUP 属性。|  
|GETATTRFLAG_THIS|0x0100|标识具有 SOURCETEXT_ATTR_THIS 属性的当前对象。|  
|GETATTRFLAG_HUMANTEXT|0x8000|标识具有 SOURCETEXT_ATTR_HUMANTEXT 特性的字符串内容和注释文本。|  
  
 `pattr`  
 [传入、 传出 size_is (`cch`)] 的脚本块代码的颜色信息。  
  
## <a name="return-value"></a>返回值  
 一个 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptAuthor 接口](../../winscript/reference/iactivescriptauthor-interface.md)   
 [SOURCE_TEXT_ATTR 枚举](../../winscript/reference/source-text-attr-enumeration.md)