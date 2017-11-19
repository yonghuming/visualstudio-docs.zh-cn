---
title: "IDebugExpressionContext::ParseLanguageText |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugExpressionContext.ParseLanguageText
apilocation: jscript.dll
helpviewer_keywords: IDebugExpressionContext::ParseLanguageText
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e455768b7d38096c64ab61f2b36aeba871ddf0bc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressioncontextparselanguagetext"></a>IDebugExpressionContext::ParseLanguageText
创建一个调试表达式指定的文本。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT ParseLanguageText(  
   LPCOLESTR           pstrCode,  
   UINT                nRadix,  
   LPCOLESTR           pstrDelimiter,  
   DWORD               dwFlags,  
   IDebugExpression**  ppe  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pstrCode`  
 [in]提供的表达式或语句的文本。  
  
 `nRadix`  
 [in]若要使用的基数。  
  
 `pstrDelimiter`  
 [in]结束的脚本块分隔符中。 当`pstrCode`分析从文本流，则主机通常将使用一个分隔符，如两个单引号 （'），来检测脚本块的末尾。 此参数指定主机使用，从而提供某些条件的基元预处理的脚本引擎的分隔符 （例如，将作为分隔符用于两个单引号替换单引号 [']）。 完全如何 （和如果） 此信息取决于脚本引擎的脚本引擎使用。 将此参数设置为`NULL`如果主机未使用分隔符来标记的脚本块的结尾。  
  
 `dwFlags`  
 [in]以下的调试文本标志的组合：  
  
|常量|值|描述|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|指示该文本是而不是语句表达式。 此标志可能会影响某些语言分析文本时的方式。|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|如果返回值可用时，它将使用由调用方。|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|不允许副作用。 如果设置此标志，对表达式求值应更改任何运行时状态。|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|允许文本求值时的断点。 如果未设置此标志，断点将会忽略文本求值时。|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|文本的求值时允许错误报告。 如果未设置此标志，然后将不报告错误到主机求值时。|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|指示表达式的计算结果是代码上下文，而不是运行该表达式本身|  
  
 `ppe`  
 [out]返回指定的文本的调试表达式。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法创建一个调试表达式。 指定的文本。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugExpressionContext 接口](../../winscript/reference/idebugexpressioncontext-interface.md)