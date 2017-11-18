---
title: "无符号右移位赋值运算符 (&gt;&gt;&gt;=) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '>>>='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>>>= operator'
- unsigned right shift assignment operator (>>>=)
- assignment operators, JavaScript
ms.assetid: f67c3737-7d39-41ae-9c11-8b16d38f6179
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1272cbb58645df605743c6790642cd0e295442aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="unsigned-right-shift-assignment-operator-gtgtgt-javascript"></a>无符号右移位赋值运算符 (&gt;&gt;&gt;=) (JavaScript)
按表达式值中指定的位数右移变量值（不保留符号），并将结果赋给变量。  
  
## <a name="syntax"></a>语法  
  
```  
  
result >>>= expression  
```  
  
## <a name="parameters"></a>参数  
 *结果*  
 任何变量。  
  
 *表达式*  
 任何表达式。  
  
## <a name="remarks"></a>备注  
 使用 >>> = 运算符是完全相同的方式执行以下操作：  
  
```JavaScript  
result = result >>> expression  
```  
  
 **>>>=** 运算符将位右移*结果*右旋转中指定的比特数*表达式*。 从左侧填充零。 移出右侧的数字将被丢弃。 例如:   
  
```JavaScript  
var temp  
temp = -14  
temp >>>= 2  
```  
  
 变量*temp* -14 (11111111 2 的补数二进制 11111111 11111111 11110010) 的初始值。 当右移两位，值将等于 1073741820 (00111111 二进制 11111111 11111111 11111100)。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [无符号右移位运算符 (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [按位左移运算符 (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [按位右移运算符 (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)