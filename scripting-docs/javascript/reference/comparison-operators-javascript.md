---
title: "比较运算符 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Comparison
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- comparison operators, script
- greater than operator
- comparison operators
- greater than or equal to operator
- inequity operator
- identity operator
ms.assetid: 084f90f0-d010-47cf-96dd-13d637fc9b68
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 067d570523fc2241b4f2e0442785a49aedb15200
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="comparison-operators-javascript"></a>比较运算符 (JavaScript)
返回指示比较结果的布尔值。  
  
## <a name="syntax"></a>语法  
  
```  
  
expression1 comparisonoperator expression2  
```  
  
## <a name="parameters"></a>参数  
 `expression1`  
 任何表达式。  
  
 `comparisonoperator`  
 任何比较运算符。  
  
 `expression2`  
 任何表达式。  
  
## <a name="remarks"></a>备注  
 比较字符串时[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]使用 Unicode 字符值的字符串表达式。  
  
 下面介绍了不同组的运算符根据的类型和值的行为方式`expression1`和`expression2`:  
  
 关系运算符： `<`， `>`， `<=`，`>=`  
  
-   尝试转换同时`expression1`和`expression2`为数字。  
  
-   如果两个表达式都是字符串，请执行字符串比较。  
  
-   如果其中任何一个表达式是`NaN`，则返回`false`。  
  
-   负零等于正零。  
  
-   负无穷大小于包括它自身的所有内容。  
  
-   正无穷大大于包括它自身的所有内容。  
  
 相等运算符： `==`，`!=`  
  
-   如果两个表达式的类型不同，尝试将它们转换为字符串、 数字、 或布尔值。  
  
-   `NaN`不等于任何内容包括它自身。  
  
-   负零等于正零。  
  
-   `null`等于同时`null`和`undefined`。  
  
-   值被视为相等，如果它们是相同的字符串、 数值上相等的数字，同一个对象相同的布尔值，或 (如果不同的类型) 它们可以强制转换为哪一种情况。  
  
-   每个其他比较被视为不相等。  
  
 标识运算符： `===`，`!==`  
  
 这些运算符的行为相同相等运算符，只不过不完成任何类型的转换。 如果这两个表达式的类型不相同，这些表达式始终返回`false`。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)