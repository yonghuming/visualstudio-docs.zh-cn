---
title: "Math.abs 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: abs
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- absolute values, calculating
- absolute values
- numeric expressions
- abs method
ms.assetid: 9af4b5b8-de77-47bb-bb59-abdde371e4c3
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5719905a7de375f1b409378f0579e3d8b25209fc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="mathabs-function-javascript"></a>Math.abs 函数 (JavaScript)
返回一个数字 （而不考虑它是否是正数或负数的值） 的绝对值。 例如，-5 的绝对值的数值是 5 的绝对值的数值相同。  
  
## <a name="syntax"></a>语法  
  
```  
Math.abs(number)  
```  
  
#### <a name="parameters"></a>参数  
 所需`number`自变量是数值表达式，它需要绝对值的数值。  
  
## <a name="return-value"></a>返回值  
 绝对值的数值的`number`自变量。  
  
## <a name="example"></a>示例  
 下面的示例阐释了 `abs` 函数的用法。  
  
```JavaScript  
var s;  
var v1 = Math.abs(6);  
var v2 = Math.abs(-6);  
if (v1 == v2) {  
    document.write("Absolute values are the same.");  
}  
else {  
document.write("Absolute values are different.");  
}  
  
// Output: Absolute values are the same.  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**: [Math 对象](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [Math 对象](../../javascript/reference/math-object-javascript.md)