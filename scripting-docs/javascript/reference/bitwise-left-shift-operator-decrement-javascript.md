---
title: "按位左移运算符 (&lt;&lt;) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: <<
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- << operator
- left shift operators
- << operator, about << operator
- bitwise operators, Left Shift operator
ms.assetid: 18148596-7b86-4add-aeef-106991c69435
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d63fc50659695f518e581edbed67c009b36577f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-left-shift-operator-ltlt-javascript"></a>按位左移运算符 (&lt;&lt;) (JavaScript)
左移表达式的位。  
  
## <a name="syntax"></a>语法  
  
```  
  
result = expression1 << expression2  
```  
  
## <a name="parameters"></a>参数  
 *结果*  
 任何变量。  
  
 *expression1*  
 任何表达式。  
  
 *expression2*  
 任何表达式。  
  
## <a name="remarks"></a>备注  
 **<<** 运算符将位右移*expression1*中指定的位数左*expression2*。 例如:   
  
```JavaScript  
var temp  
temp = 14 << 2  
```  
  
 变量*temp*的值为 56，因为 14 (即二进制的 00001110) 移左的两位等于 56 (即 00111000 以二进制形式)。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [左移赋值运算符 (<\<=)](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)   
 [按位右移运算符 (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [无符号右移位运算符 (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)