---
title: "逻辑非运算符 （！）(JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '!'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Logical NOT operator
- '! operator'
- '! operator, about ! operator'
ms.assetid: 68c3dc71-ae95-4293-9155-67405846d71d
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29c27b9cd670989eb2112de5067e68bd09d76903
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="logical-not-operator--javascript"></a>逻辑“非”运算符 (!)(JavaScript)
对表达式执行逻辑求反。  
  
## <a name="syntax"></a>语法  
  
```  
  
result = !expression  
```  
  
## <a name="parameters"></a>参数  
 *结果*  
 任何变量。  
  
 *表达式*  
 任何表达式。  
  
## <a name="remarks"></a>备注  
 下表说明了如何*结果*确定。  
  
|如果`expression`是|然后`result`是|  
|------------------------|----------------------|  
|True|False|  
|False|True|  
  
 所有的一元运算符，如**！** 运算符，计算表达式的值，如下所示：  
  
-   如果应用于未定义或`null`引发表达式，运行时错误。  
  
-   对象将转换为字符串。  
  
-   如果可能，将字符串转换为数字。 否则，将引发运行时错误。  
  
-   布尔值被视为数字 （0，如果为 false，1，如果为 true）。  
  
 运算符应用于结果数字。  
  
 有关**！** 运算符，如果*表达式*不为零，*结果*为零。 如果*表达式*为零，*结果*为 1。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [按位 NOT 运算符 （~）](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)