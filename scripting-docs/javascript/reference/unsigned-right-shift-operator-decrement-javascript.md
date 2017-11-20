---
title: "无符号右移位运算符 (&gt;&gt;&gt;) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '>>>'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- unsigned right shift operator (>>>)
- '>>> operator'
ms.assetid: df48bdfc-8741-46ab-b681-449da57ac95c
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: efb873bedc0a64089c7ec892d6378b4869c0ca21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="unsigned-right-shift-operator-gtgtgt-javascript"></a>无符号右移位运算符 (&gt;&gt;&gt;) (JavaScript)
右移表达式的位无符号。  
  
## <a name="syntax"></a>语法  
  
```  
  
result = expression1 >>> expression2  
```  
  
## <a name="parameters"></a>参数  
 *结果*  
 任何变量。  
  
 *expression1*  
 任何表达式。  
  
 *expression2*  
 任何表达式。  
  
## <a name="remarks"></a>备注  
 **>>>** 运算符将位右移*expression1*右旋转中指定的比特数*expression2*。 从左侧填充零。 移出右侧的数字将被丢弃。 例如:   
  
```JavaScript  
var temp  
temp = -14 >>> 2  
```  
  
 变量*temp*的初始值-14 (11111111 2 的补数二进制 11111111 11111111 11110010)。 右移的两位时，值将等于 1073741820 (00111111 二进制 11111111 11111111 11111100)。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [无符号右移位赋值运算符 (>>> =)](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)   
 [按位左移运算符 (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [按位右移运算符 (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)