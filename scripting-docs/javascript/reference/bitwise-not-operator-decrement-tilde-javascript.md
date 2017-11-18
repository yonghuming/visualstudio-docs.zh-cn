---
title: "按位 NOT 运算符 （~） (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ~
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- NOT operator
- bitwise operators, NOT operator
ms.assetid: 39f92474-fe05-4a8b-9ad8-caca93f82bca
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aec64b055b260efb7a4b0d952aed9b3a5d7ddc82
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-not-operator--javascript"></a>按位取反运算符 (~) (JavaScript)
对表达式执行按位“取非”（求反）。  
  
## <a name="syntax"></a>语法  
  
```  
  
result = ~ expression  
```  
  
## <a name="parameters"></a>参数  
 *结果*  
 任何变量。  
  
 *表达式*  
 任何表达式。  
  
## <a name="remarks"></a>备注  
 所有的一元运算符，如`~`运算符，计算表达式，如下所示：  
  
-   如果应用于未定义或`null`引发表达式，运行时错误。  
  
-   对象将转换为字符串。  
  
-   如果可能，将字符串转换为数字。 否则，将引发运行时错误。  
  
-   布尔值被视为数字 （0，如果为 false，1，如果为 true）。  
  
 运算符应用于结果数字。  
  
 `~`运算符审视的二进制表示形式的表达式的值，并执行按位求反运算。  
  
 为 1 的表达式中的任何数字将成为在结果为 0。 任何表达式中为 0 的数字将成为结果中的 1。  
  
 下面的示例演示了使用的按位 NOT （~） 运算符。  
  
```  
var temp = ~5;  
```  
  
 生成的值是-6 下, 表中所示。  
  
|Expression|二进制值 （2 的补数）|十进制值|  
|----------------|---------------------------------------|-------------------|  
|5|00000000 00000000 00000000 00000101|5|  
|~5|11111111 11111111 11111111 11111010|-6|  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [逻辑非运算符 （！）](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)