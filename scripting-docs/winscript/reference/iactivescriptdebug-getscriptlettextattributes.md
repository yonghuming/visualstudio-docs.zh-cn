---
title: "IActiveScriptDebug::GetScriptletTextAttributes |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptDebug.GetScriptletTextAttributes
apilocation: jscript.dll
helpviewer_keywords: IActiveScriptDebug::GetScriptletTextAttributes
ms.assetid: b3990d86-5fdf-4c9f-9678-3f4b808c7ca8
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 909879030e5c6d26353d2003279d5c1ca7bacb74
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptdebuggetscriptlettextattributes"></a>IActiveScriptDebug::GetScriptletTextAttributes
返回任意 scriptlet 的文本属性。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pstrCode`  
 [in]Scriptlet 文本中。 此字符串不需要终止 null。  
  
 `uNumCodeChars`  
 [in]中的 scriptlet 文本的字符数。  
  
 `pstrDelimiter`  
 [in]最终的 scriptlet 分隔符的地址。 当`pstrCode`分析从文本流中，主机通常使用分隔符，如两个单引号 （'），来检测的 scriptlet 尾。 此参数指定主机使用，从而提供某些条件的基元预处理的脚本引擎的分隔符 （例如，将作为分隔符用于两个单引号替换单引号 [']）。 完全如何 （和如果） 此信息取决于脚本引擎的脚本引擎使用。 如果主机未使用分隔符来标记的 scriptlet 的结尾，此参数设置为 NULL。  
  
 `dwFlags`  
 [in]与 scriptlet 关联的标志。 可以是这些值的组合：  
  
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
  
## <a name="remarks"></a>备注  
 实现智能宿主`IDebugDocumentText`接口可以使用此方法委托到调用`IDebugDocumentText::GetText`方法。  
  
 提供此调用，因为 scriptlet 往往是表达式，并且可能具有不同的语法比脚本块。 如果他们具有相同的语法，此方法的实现将相同的实现`GetScriptTextAttributes`方法。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptDebug 接口](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)   
 [IDebugDocumentText 接口](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE_TEXT_ATTR 枚举](../../winscript/reference/source-text-attr-enumeration.md)