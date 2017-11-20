---
title: "逻辑与运算符 (&amp;&amp;) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '&&'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- logical AND operator
- '&& operator'
ms.assetid: 4714dea9-1999-444a-8acd-72f0851e4f65
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2107eb89c5ca964cf08172050b49307cb150590f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="logical-and-operator-ampamp-javascript"></a>逻辑与运算符 (&amp;&amp;) (JavaScript)
对两个表达式执行逻辑与运算。  
  
## <a name="syntax"></a>语法  
  
```  
  
result = expression1 && expression2   
```  
  
## <a name="parameters"></a>参数  
 `result`  
 任何变量。  
  
 `expression1`  
 任何表达式。  
  
 `expression2`  
 任何表达式。  
  
## <a name="remarks"></a>备注  
 如果 `expression1` 的计算结果为 `false`，则 `result` 为 `expression1`。 否则 `result` 是 `expression2`。 因此，如果两个操作数都为 true，则该操作返回 `true`；否则，返回 `false`。  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 使用下列规则将非布尔值转换为布尔值：  
  
-   所有对象都被视为 `true`。  
  
-   如果字符串为空，则它们会被视为 `false`。  
  
-   `null` 和 `undefined` 被视为 `false`。  
  
-   如果数字为零，则它为 `false`。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)