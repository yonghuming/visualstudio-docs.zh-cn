---
title: "&#39; 返回 &#39;语句在函数之外 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07b633c87dc11b291a5a5783f8121b2a368996d6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="39return39-statement-outside-of-function"></a>&#39; 返回 &#39;语句在函数之外
你使用`return`语句在全局范围内的代码。 `return`语句应仅出现在函数体。  
  
 调用具有函数`()`运算符是一个表达式。 所有表达式都具有的值;`return`语句用于指定函数所返回的值。 常规格式为：  
  
```  
  
return [ expression ];  
```  
  
 当`return`执行语句，*表达式*计算并将其作为函数的值返回。 如果没有任何表达式，**未定义**返回。  
  
 停止执行函数时`return`执行语句，即使有仍保留在函数体中其他语句。 此规则的例外是如果**返回**语句出现在**重**块，并且没有相应**最后**，代码中阻止**最后**函数返回前，将执行块。  
  
 如果函数返回，因为无需执行到达函数体的结尾`return`语句，返回的值是**未定义**（这意味着函数结果不能作为较大的表达式的一部分的值).  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   删除`return`从你的代码 （全局范围） 的主体的语句。  
  
## <a name="see-also"></a>另请参阅  
 [return 语句](../../javascript/reference/return-statement-javascript.md)   
 [函数对象](../../javascript/reference/function-object-javascript.md)   
 [caller 属性 (Function)](../../javascript/reference/caller-property-function-javascript.md)