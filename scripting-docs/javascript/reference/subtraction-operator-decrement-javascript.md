---
title: "减法运算符 （-） (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '-'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '- operator, about - operator'
- '- operator'
- negation operator
- subtraction operator, syntax
- arithmetic operators, subtraction
- operators, subtraction
ms.assetid: cd0681d3-15cd-49fe-b4dd-e087de55d778
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb79aab0a57c733871dbfc73ac96c7ddbf4db37c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="subtraction-operator---javascript"></a>减法运算符 (-) (JavaScript)
从另一个表达式的值中减去或提供一元求反运算的单个表达式。  
  
## <a name="syntax"></a>语法  
  
```  
  
result = number1 - number2;  
```  
  
## <a name="parameters"></a>参数  
 *结果*  
 任何数值变量。  
  
 `number`  
 任何数值表达式。  
  
 `number1`  
 任何数值表达式。  
  
 `number2`  
 任何数值表达式。  
  
## <a name="remarks"></a>备注  
 在语法 1，  **-** 运算符是用来查找两个数字之间的差异的算术减法运算符。 在语法 2，  **-** 运算符用于一元求反运算符指示表达式的负值。  
  
 对于语法 2，和所有一元运算符，计算表达式，如下所示：  
  
-   如果应用于未定义或`null`引发表达式，运行时错误。  
  
-   对象将转换为字符串。  
  
-   如果可能，将字符串转换为数字。 否则，将引发运行时错误。  
  
-   布尔值被视为数字 （0，如果为 false，1，如果为 true）。  
  
 运算符应用于结果数字。 在语法 2 中，如果结果的数字不为零，*结果*等于符号颠倒得到数。 如果生成的数字为零，*结果*为零。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [减法赋值运算符 （-）](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)