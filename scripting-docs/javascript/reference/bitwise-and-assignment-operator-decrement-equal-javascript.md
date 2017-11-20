---
title: "按位 AND 赋值运算符 (&amp;=) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '&='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '&= operator'
- assignment operators, bitwise [JavaScript]
- AND operator
- bitwise operators, AND operator
ms.assetid: e7e2eabb-4fc1-4fdc-9dd8-1e6d715371fa
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dfd2a77e66296cafc6c8403570f0536e1333e081
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-and-assignment-operator-amp-javascript"></a>按位 AND 赋值运算符 (&amp;=) (JavaScript)
设置变量的值按位与运算的结果和表达式的值。 变量和表达式被视为 32 位整数。  
  
## <a name="syntax"></a>语法  
  
```  
  
result &= expression  
```  
  
## <a name="parameters"></a>参数  
 `result`  
 任何变量。  
  
 `expression`  
 任何表达式。  
  
## <a name="remarks"></a>备注  
 使用此运算符是与指定相同的：  
  
```JavaScript  
result = result & expression  
```  
  
 [按位 AND 运算符 (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)考察的二进制表示形式的值`result`和`expression`，并执行按位 AND 运算。 此操作的输出类似于：  
  
```JavaScript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
expr1 &= expr2;  
  
document.write(expr1);  
```  
  
 任何时候，只要两个表达式中的位，结果中的该位已 1。 否则，结果中的该位具有为 0。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [按位与运算符 (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)