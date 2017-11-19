---
title: "IDebugDocumentHost::GetScriptTextAttributes |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHost.GetScriptTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: IDebugDocumentHost::GetScriptTextAttributes
ms.assetid: fe459d0d-937f-4176-be81-99d5cca121a1
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 517b228bb46594d19ba6d2fdf41a68e22ac03c75
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthostgetscripttextattributes"></a>IDebugDocumentHost::GetScriptTextAttributes
返回文档文本块的文本属性。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pstrCode`  
 [in]脚本块文本。 不需要此字符串不为 null 终止。  
  
 `uNumCodeChars`  
 [in]中的脚本块文本的字符数。  
  
 `pstrDelimiter`  
 [in]结束的脚本块分隔符的地址。 当`pstrCode`分析从文本流，则主机通常将使用一个分隔符，如两个单引号 （'），来检测脚本块的末尾。 此参数指定主机使用，从而提供某些条件的基元预处理的脚本引擎的分隔符 （例如，将作为分隔符用于两个单引号替换单引号 [']）。 完全如何 （和如果） 此信息取决于脚本引擎的脚本引擎使用。 如果主机未使用分隔符来标记的脚本块的结尾，此参数设置为 NULL。  
  
 `dwFlags`  
 [in]与脚本块关联的标志。 可以是这些值的组合：  
  
|常量|值|描述|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|从 0x0001|指示标识符和圆点运算符应标识的 SOURCETEXT_ATTR_IDENTIFIER 和 SOURCETEXT_ATTR_MEMBERLOOKUP 标志，分别。|  
|GETATTRFLAG_THIS|0x0100|指示当前对象的标识符应使用 SOURCETEXT_ATTR_THIS 标志来标识。|  
|GETATTRFLAG_HUMANTEXT|0x8000|指示应使用 SOURCETEXT_ATTR_HUMANTEXT 标志标识字符串内容和注释文本。|  
  
 `pattr`  
 [在中，out]要包含返回的特性的缓冲区。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_NOTIMPL`|主机使用只有默认属性。|  
  
## <a name="remarks"></a>备注  
 此方法返回文档文本的任意块的文本属性。 它是可接受的主机返回`E_NOTIMPL`，在这种情况下使用默认属性。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugDocumentHost 接口](../../winscript/reference/idebugdocumenthost-interface.md)   
 [SOURCE_TEXT_ATTR 枚举](../../winscript/reference/source-text-attr-enumeration.md)