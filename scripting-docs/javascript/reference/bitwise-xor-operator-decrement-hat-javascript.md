---
title: "按位异或运算符 (^) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ^
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- bitwise operators, XOR operator
- XOR operator
ms.assetid: 44ef0d18-abb5-4d83-9e77-6394635b3f48
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ebe8ff9805793bf306688622b0b29007b1562e2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-xor-operator--javascript"></a>按位异或运算符 (^) (JavaScript)
对两个表达式执行按位“异或”。  
  
## <a name="syntax"></a>语法  
  
```  
  
result = expression1 ^ expression2  
```  
  
## <a name="parameters"></a>参数  
 *结果*  
 任何变量。  
  
 *expression1*  
 任何表达式。  
  
 *expression2*  
 任何表达式。  
  
## <a name="remarks"></a>备注  
 **^** 运算符审视的二进制表示形式的两个表达式的值，并执行按位异或运算。 此操作的结果的行为，如下所示：  
  
```JavaScript  
0101   (expression1)  
1100   (expression2)  
----  
1001   (result)  
```  
  
 当且仅一个表达式只有 1 中的一个数字时，结果中的该位只有 1。 否则，结果中的该位具有为 0。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [按位异或赋值运算符 (^ =)](../../javascript/reference/bitwise-xor-assignment-operator-decrement-hat-equal-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)