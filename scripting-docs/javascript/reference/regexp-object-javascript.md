---
title: "RegExp 对象 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: RegExp
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- RegExp object, overview
- RegExp object
ms.assetid: 7f6b1073-8cbb-49ed-94b6-56833ba663c5
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7319e4556721bcfd397061ce525acfb3278c6b9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="regexp-object-javascript"></a>RegExp 对象 (JavaScript)
内部对象，它存储有关正则表达式模式的结果的信息匹配。  
  
## <a name="syntax"></a>语法  
  
```  
  
RegExp.property   
```  
  
## <a name="remarks"></a>备注  
 所需*属性*自变量可以是任何一种`RegExp`对象属性。  
  
 `RegExp`对象不能直接创建，但它是始终可供使用。 直到已完成成功的正则表达式搜索，各个属性的初始值`RegExp`对象如下所示：  
  
|属性|速记|初始值|  
|--------------|---------------|-------------------|  
|索引||-1|  
|input|$_|空字符串。|  
|lastIndex||-1|  
|lastMatch|$&|空字符串。|  
|lastParen|$+|空字符串。|  
|leftContext|$`|空字符串。|  
|rightContext|$'|空字符串。|  
|$1 - $9|$1 - $9|空字符串。|  
  
 其属性具有未定义作为它们的值，直到成功的正则表达式搜索已完成。  
  
 全局`RegExp`对象不应与混淆**正则表达式**对象。 即使它们看起来像相同的操作一样，它们彼此独立，截然不同。 全局属性`RegExp`对象包含不断更新有关每个匹配项的信息时的属性时**正则表达式**对象包含仅发生的匹配信息与该实例的**正则表达式**。  
  
## <a name="example"></a>示例  
 下面的示例执行正则表达式搜索。 它显示匹配项，并从全局 submatches`RegExp`对象，并从返回的数组`exec`方法。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
<a name="js56jsobjregexpprop"></a>   
## <a name="properties"></a>属性  
 [$1...$9 属性](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)&#124;[index 属性](../../javascript/reference/index-property-regexp-javascript.md)&#124;[input 属性](../../javascript/reference/input-property-dollar-regexp-javascript.md)&#124;[lastIndex 属性](../../javascript/reference/lastindex-property-regexp-javascript.md)&#124;[lastMatch 属性](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)&#124;[lastParen 属性](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)&#124;[leftContext 属性](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)&#124;[rightContext 属性](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)  
  
## <a name="methods"></a>方法  
 `RegExp`对象没有任何方法。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)   
 [正则表达式语法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [String 对象](../../javascript/reference/string-object-javascript.md)