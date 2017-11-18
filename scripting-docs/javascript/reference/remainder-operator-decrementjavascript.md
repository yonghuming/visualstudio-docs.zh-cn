---
title: "余数运算符 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '%'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- remainder operator, JavaScript
- '% operator [JavaScript]'
- Remainder function [JavaScript]
ms.assetid: 087d654f-623b-498d-95ff-596d26bf674d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce74b8512b25cfe215d294873102b274623b42a2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="remainder-operator-javascript"></a>余数运算符 (JavaScript)
将一个表达式的值与另一值除以并返回余数。  
  
## <a name="syntax"></a>语法  
  
```  
  
result = number1 % number2  
```  
  
## <a name="arguments"></a>参数  
 `result`  
 任何变量。  
  
 `number1`  
 任何数值表达式。  
  
 `number2`  
 任何数值表达式。  
  
## <a name="remarks"></a>备注  
 余数运算符将划分`number1`通过`number2`并返回余数作为`result`。 符号`result`的符号相同`number1`。 值`result`介于 0 和的绝对值的数值之间`number2`。  
  
 下面的代码演示如何使用余数运算符。  
  
```  
var modResult = 19 % 6.7;  
document.write(modResult);  
  
// Output: 5.6  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)
