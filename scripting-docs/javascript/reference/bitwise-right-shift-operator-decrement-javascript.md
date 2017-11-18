---
title: "按位右移运算符 (&gt;&gt;) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '>>'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>> operator'
- '>> operator, about >> operator'
- '>> operator, bitsets'
- bitwise operators, right shift operator
ms.assetid: 89dc57e0-0b0d-49a4-a8ed-56d8bb20f3e3
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70db0c176b475886a26cfe4c06f7f2f0c9d4fc2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-right-shift-operator-gtgt-javascript"></a>按位右移运算符 (&gt;&gt;) (JavaScript)
右移表达式的位保留符号。  
  
## <a name="syntax"></a>语法  
  
```  
  
result = expression1 >> expression2  
```  
  
## <a name="parameters"></a>参数  
 *结果*  
 任何变量。  
  
 *expression1*  
 任何表达式。  
  
 *expression2*  
 任何表达式。  
  
## <a name="remarks"></a>备注  
 >> 运算符将位右移*expression1*右旋转中指定的比特数*expression2*。 符号位的*expression1*用来填充从左侧的位数。 移出右侧的数字将被丢弃。 例如，在下面的代码将计算， *temp*的值为-4:-14 （即二进制的 11110010） 右移两位后等于-4 （11111100 求补二进制）。  
  
```JavaScript  
var temp  
temp = -14 >> 2  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [按位左移运算符 (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [右移赋值运算符 (>> =)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)   
 [无符号右移位运算符 (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)