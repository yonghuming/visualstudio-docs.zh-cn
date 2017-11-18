---
title: "右移赋值运算符 (&gt;&gt;=) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '>>='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>>= operator [JavaScript]'
- right shift operators [JavaScript]
- assignment operators, JavaScript
ms.assetid: 8c1f7f90-e3ac-42ee-94f2-5ccc47d7aef6
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb93d146ad00bd19c09fb4cfca3af776a11f245d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="right-shift-assignment-operator-gtgt-javascript"></a>右移赋值运算符 (&gt;&gt;=) (JavaScript)
按表达式值中指定的位数右移变量值（保留符号），并将结果赋给变量。  
  
## <a name="syntax"></a>语法  
  
```  
  
result >>= expression  
```  
  
## <a name="parameters"></a>参数  
 *结果*  
 任何变量。  
  
 *表达式*  
 任何表达式。  
  
## <a name="remarks"></a>备注  
 使用 **>>=** 运算符正是与指定相同：  
  
```JavaScript  
result = result >> expression  
```  
  
 **>>=** 运算符将位右移*结果*右旋转中指定的比特数*表达式*。 符号位的*结果*用来填充从左侧的位数。 移出右侧的数字将被丢弃。 例如，在下面的代码将计算， *temp*的值为-4: 14 (即二进制的 11110010) 右移两位后等于-4 (11111100)。  
  
```JavaScript  
var temp  
temp = -14  
temp >>= 2  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [按位左移运算符 (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [按位右移运算符 (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [无符号右移位运算符 (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)