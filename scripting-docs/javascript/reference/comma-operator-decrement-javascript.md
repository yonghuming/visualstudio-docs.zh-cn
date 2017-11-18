---
title: "逗号运算符 （，） (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '%2C'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: comma operator
ms.assetid: 699fa0bf-cd0a-45ee-a291-2fbed4ecd470
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cb504beefc5ce4c260ec8296e2cf097e17d349e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="comma-operator--javascript"></a>逗号运算符 (,) (JavaScript)
使两个表达式按顺序执行。  
  
## <a name="syntax"></a>语法  
  
```  
  
expression1, expression2  
```  
  
## <a name="parameters"></a>参数  
 `expression1`  
 任何表达式。  
  
 `expression2`  
 任何表达式。  
  
## <a name="remarks"></a>备注  
 `,`运算符使表达式以按从左到右的顺序执行。 一个常见用途`,`运算符是递增表达式中`for`循环。 例如：  
  
```JavaScript  
j=25;  
for (i = 0; i < 10; i++, j++)  
{  
   k = i + j;  
}  
```  
  
 `for`语句允许仅在每次通过循环的结尾处执行的单个表达式。 `,`运算符允许多个表达式被视为单个表达式，因此可以递增两个变量。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [for 语句](../../javascript/reference/for-statement-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)