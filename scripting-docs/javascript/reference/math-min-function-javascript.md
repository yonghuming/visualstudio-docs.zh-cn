---
title: "Math.min 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: min
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: min method
ms.assetid: a1d7dd85-27ef-45cd-aa2a-f8e80f0b2898
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb496cff65db11cf6c99d6a6e687f39e20ea857c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="mathmin-function-javascript"></a>Math.min 函数 (JavaScript)
返回较小的一组数值表达式。  
  
## <a name="syntax"></a>语法  
  
```  
Math.min([number1[, number2[... [,numberN]]]])  
```  
  
## <a name="remarks"></a>备注  
 可选`number1, number2, ..., numberN`参数是要进行求值的数值表达式。  
  
 如果未不提供任何参数，返回的值等于[Number.POSITIVE_INFINITY](../../javascript/reference/number-constants-javascript.md)。 如果任何参数为`NaN`，返回值也为`NaN`。  
  
## <a name="example"></a>示例  
 下面的代码演示如何获取较小的两个表达式。  
  
```JavaScript  
var x = Math.min(107 - 3, 48 * 90);  
document.write(x);  
  
// Output:  
// 104  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [Math.max 函数](../../javascript/reference/math-max-function-javascript.md)