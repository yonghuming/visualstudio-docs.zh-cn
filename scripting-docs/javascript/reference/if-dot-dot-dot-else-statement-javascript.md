---
title: "如果 … else 语句 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- else_JavaScriptKeyword
- if_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- if statement, if...else
- loop structures, if...else statements
ms.assetid: dfbe86e8-9c1e-4ef5-bb9c-7d1db7ce2506
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fad12b970f69a15040acb59195f957a2a6eec3e0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ifelse-statement-javascript"></a>if...else 语句 (JavaScript)
根据表达式的值有条件地执行一组语句。  
  
## <a name="syntax"></a>语法  
  
```  
if (condition1) {  
    statement1  
}  
[else if (condition2) {  
    statement2  
}]  
[else {  
    statement3]   
}]  
```  
  
## <a name="parameters"></a>参数  
 `condition1`  
 必需。 布尔表达式。 如果`condition1`是`null`或`undefined`，`condition1`将被视为`false`。  
  
 `statement1`  
 可选。 如果执行的语句`condition1`是**true**。 可以是复合语句。  
  
 `condition2`  
 要评估的条件。  
  
 `statement2`  
 可选。 如果执行的语句`condition2`是`true`。 可以是复合语句。  
  
 `statement3`  
 如果这两个`condition1`和`condition2`是`false`，执行此语句。  
  
## <a name="example"></a>示例  
 下面的代码演示如何使用`if`， `if else`，和`else`。  
  
 很好的做法括起`statement1`和`statement2`在大括号 （{}） 为清楚起见并避免意外错误。  
  
```JavaScript  
var z = 3;  
if (x == 5) {  
    z = 10;  
}  
else if (x == 10) {  
    z = 15;  
}  
else {  
    z = 20;  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [条件（三元）运算符 (?:)](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)