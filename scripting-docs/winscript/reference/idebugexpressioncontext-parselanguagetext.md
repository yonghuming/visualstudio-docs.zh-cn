---
title: "IDebugExpressionContext::ParseLanguageText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpressionContext.ParseLanguageText
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpressionContext::ParseLanguageText"
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionContext::ParseLanguageText
创建指定文本的调试表达式。  
  
## 语法  
  
```  
HRESULT ParseLanguageText(  
   LPCOLESTR           pstrCode,  
   UINT                nRadix,  
   LPCOLESTR           pstrDelimiter,  
   DWORD               dwFlags,  
   IDebugExpression**  ppe  
);  
```  
  
#### 参数  
 `pstrCode`  
 \[out\]提供表达式或语句的文本。  
  
 `nRadix`  
 \[in\]使用基数。  
  
 `pstrDelimiter`  
 \[in\]关闭脚本块分隔符。  当 `pstrCode` 从文本时流进行分析，宿主通常使用一个分隔符，例如两个引号\("\)，检测末尾的脚本块。  此参数指定例如使用的主机，允许脚本引擎提供某些条件原始预处理的分隔符\(，一个单引号\[ \] “将两个单引号用作分隔符\)。  \(和\)，如果脚本引擎正确如何使用此信息取决于脚本引擎。  如果宿主不使用一个分隔符指示末尾的脚本块，将此参数设置为 `NULL`。  
  
 `dwFlags`  
 \[in\]组合的以下调试文本标记：  
  
|常量|值|说明|  
|--------|-------|--------|  
|DEBUG\_TEXT\_ISEXPRESSION|0x00000001|指示该文本是表达式与语句相对。  此标记会影响该文本由某些语言分析的方式。|  
|DEBUG\_TEXT\_RETURNVALUE|0x00000002|如果返回值可用，它将被调用方使用。|  
|DEBUG\_TEXT\_NOSIDEEFFECTS|0x00000004|不要允许副作用。  如果此标志设置，该表达式的计算不应更改运行时状态。|  
|DEBUG\_TEXT\_ALLOWBREAKPOINTS|0x00000008|在文本的计算时允许断点。  如果此标志未设置断点在文本的计算期间被忽略。|  
|DEBUG\_TEXT\_ALLOWERRORREPORT|0x00000010|在文本的计算时允许错误报告。  如果此标志未设置错误未向宿主报告在计算时。|  
|DEBUG\_TEXT\_EVALUATETOCODECONTEXT|0x00000020|指示该表达式将计算为代码上下文\(而非运行该表达式|  
  
 `ppe`  
 \[in\]返回指定文本的调试表达式。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法创建指定文本的调试表达式。  
  
## 请参阅  
 [IDebugExpressionContext 接口](../../winscript/reference/idebugexpressioncontext-interface.md)