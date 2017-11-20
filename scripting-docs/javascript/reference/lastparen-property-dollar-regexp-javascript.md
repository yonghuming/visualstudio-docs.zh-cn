---
title: "lastParen 属性 （$ +） (RegExp) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: $+
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: lastParen property ($+)
ms.assetid: 18aca591-a97a-48da-8b06-422346804b16
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 059cfc6556873d770798eff59bf7415426526626
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="lastparen-property--regexp-javascript"></a>JavaScriptlastParen 属性 ($+) (RegExp) (JavaScript)
如果有任何正则表达式搜索，从返回的最后一个用圆括号括起来子匹配项。 只读。  
  
## <a name="syntax"></a>语法  
  
```  
  
RegExp.lastParen  
```  
  
## <a name="remarks"></a>备注  
 此属性与关联的对象始终是全局`RegExp`对象。  
  
 初始值`lastParen`属性为空字符串。 值`lastParen`属性更改时将生成一个成功匹配。  
  
## <a name="example"></a>示例  
 下面的示例演示 `lastParen` 属性的用法：  
  
```JavaScript  
// Create the regular expression pattern.  
var re = new RegExp("d(b+)(d)","ig");  
var str = "cdbBdbsbdbdz";  
  
// Perform the search.  
var arr = re.exec(str);  
  
// Print the output.  
var s = ""   
s += "$1: " + RegExp.$1 + "<br />";  
s += "$2: " + RegExp.$2 + "<br />";  
s += "$3: " + RegExp.$3 + "<br />";  
s += "input: " + RegExp.input + "<br />";  
s += "lastMatch: " + RegExp.lastMatch + "<br />";  
s += "leftContext: " + RegExp.leftContext + "<br />";  
s += "rightContext: " + RegExp.rightContext + "<br />";   
s += "lastParen: " + RegExp.lastParen + "<br />";  
  
document.write(s);  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**: [RegExp 对象](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [$1...$9 属性 (RegExp)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)   
 [索引属性 (RegExp)](../../javascript/reference/index-property-regexp-javascript.md)   
 [input 属性 ($_) (RegExp)](../../javascript/reference/input-property-dollar-regexp-javascript.md)   
 [lastIndex 属性 (RegExp)](../../javascript/reference/lastindex-property-regexp-javascript.md)   
 [lastMatch 属性 ($&) (RegExp)](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)   
 [leftContext 属性 ($') (RegExp)](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)   
 [rightContext 属性 ($') (RegExp)](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)