---
title: "左移赋值运算符 (&lt;&lt;=) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: <<=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- <<= operator [JavaScript]
- left shift assignment operator (<<=) [JavaScript]
- left shift operators [JavaScript]
- assignment operators, JavaScript
ms.assetid: 9f30ff46-48cc-4931-b260-edef31ff0076
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf00545947f6a84f99c519fcbed887b84c179fb5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="left-shift-assignment-operator-ltlt-javascript"></a>左移赋值运算符 (&lt;&lt;=) (JavaScript)
向左移动指定的数量的位，并将结果赋给`result`。 该操作因空出的位将填入 0。  
  
## <a name="syntax"></a>语法  
  
```  
  
result <<= expression  
```  
  
## <a name="parameters"></a>参数  
 `result`  
 任何变量。  
  
 `expression`  
 要移动的位数数。  
  
## <a name="remarks"></a>备注  
 使用`<<=`运算符是与指定相同`result = result << expression`  
  
 以下示例演示如何使用 `<<=` 运算符。  
  
```JavaScript  
// 14 is 00000000000000000000000000001110  
var temp = 14;  
temp <<= 2;   
document.write(temp);  
// 56 is 00000000000000000000000000111000  
Output: 56  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [按位左移运算符 (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [按位右移运算符 (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [无符号右移位运算符 (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)