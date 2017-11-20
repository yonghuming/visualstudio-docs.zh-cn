---
title: "Math 常量 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- LN2 constant [JavaScript]
- E constant [JavaScript]
- LOG10E constant [JavaScript]
- SQRT1_2 constant [JavaScript]
- LOG2E constant [JavaScript]
- Math.SQRT2 constant [JavaScript]
- PI constant [JavaScript]
- Math.LOG2E constant [JavaScript]
- constants [JavaScript], math
- Math.E constant [JavaScript]
- logarithm consants [JavaScript]
- Math.LOG10E constant [JavaScript]
- Math.SQRT1_2 constant [JavaScript]
- SQRT2 constant [JavaScript]
- square root constants [JavaScript]
- Math.PI constant [JavaScript]
- math constants [JavaScript]
- LN10 constant [JavaScript]
- Math.LN2 constant [JavaScript]
- Math.LN10 constant [JavaScript]
ms.assetid: 8a674046-cb99-4103-92be-83697fba6344
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9942abb69af416cd4cd7f092dc9f1478e0bc3a69
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="math-constants-javascript"></a>Math 常量 (JavaScript)
Math 常量返回的属性的常量值`Math`对象。  
  
## <a name="math-object-constants"></a>数学对象常量  
 下表列出的常量值的属性[Math 对象](../../javascript/reference/math-object-javascript.md)。  
  
|返回的常量|描述|估计值|  
|--------------|-----------------|-----------------------|  
|`Math.E`|数学常数 e。 这是欧拉数，自然对数的底。|2.718|  
|`Math.LN2`|2 的自然对数。|0.693|  
|`Math.LN10`|10 的自然对数。|2.302|  
|`Math.LOG2E`|以 2 为底 e 的对数。|1.443|  
|`Math.LOG10E`|以 10 为底 e 的对数。|0.434|  
|`Math.PI`|Pi。 这是圆的周长与直径的比率。|3.14159|  
|`Math.SQRT1_2`|0.5 的平方根，或相当于 1 除以 2 的平方根。|0.707|  
|`Math.SQRT2`|2 的平方根。|1.414|  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`Math.PI`常量。  
  
```JavaScript  
var radius = 3;  
var area = Math.PI * radius * radius;  
document.write(area);  
  
// Output: 28.274333882308138  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**: [Math 对象](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [Number 常量](../../javascript/reference/number-constants-javascript.md)   
 [JavaScript 常量](../../javascript/reference/javascript-constants.md)