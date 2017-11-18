---
title: "Number 常量 (JavaScript) |Microsoft 文档"
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
- POSITIVE_INFINITY constant [JavaScript]
- MAX_VALUE constant [JavaScript]
- MIN_VALUE constant [JavaScript]
- number constants [JavaScript]
- Number.NEGATIVE_INFINITY constant [JavaScript]
- Number.POSITIVE_INFINITY constant [JavaScript]
- NEGATIVE_INFINITY constant [JavaScript]
- NaN constant [JavaScript]
- Number.MIN_VALUE constant [JavaScript]
- constants [JavaScript], number
- Number.NaN constant [JavaScript]
- Number.MAX_VALUE constant [JavaScript]
ms.assetid: e0701b41-99ae-4916-9ec0-f79bb15386fb
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f846ef7cbd9609f7913d6305e48cb4942476ca21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="number-constants-javascript"></a>Number 常量 (JavaScript)
以下数字常量是 `Number` 对象的属性。  
  
## <a name="number-object-constants"></a>Number 对象常量  
 您不必创建 `Number` 对象来访问这些常量。  
  
|常量|值|  
|--------------|--------------------|  
|`Number.EPSILON`|可以在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中表示的最小数。 大约等于 2.2204460492503130808472633361816E-16。|  
|`Number.MAX_SAFE_INTEGER`|可在 JavaScript 中安全表示的最大数。 等于 9007199254740991。|  
|`Number.MAX_VALUE`|可以在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中表示的最大数。 大约等于 1.79E+308。|  
|`Number.MIN_SAFE_INTEGER`|可在 JavaScript 中安全表示的最小数。 等于-9007199254740991。|  
|`Number.MIN_VALUE`|可以在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中表示的最接近零的数。 大约等于 5.00E-324。|  
|`Number.NaN`|不是数字的值。<br /><br /> 在相等比较中，`NaN` 不等于任何值，包括它自身。 若要测试该值是否等效于`NaN`，使用[isNaN 函数](../../javascript/reference/isnan-function-javascript.md)。|  
|`Number.NEGATIVE_INFINITY`|可以在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中表示的、小于最大负数的值。<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 将 `NEGATIVE_INFINITY` 值显示为 `-infinity`。|  
|`Number.POSITIVE_INFINITY`|可以在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中表示的、大于最大数的值。<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 将 `POSITIVE_INFINITY` 值显示为 `infinity`。|  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 对于 `Number.EPSILON`、`Number.MAX_SAFE_INTEGER` 和 `Number.MIN_SAFE_INTEGER`：  
  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **适用于**: [Number 对象](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [Math 常量](../../javascript/reference/math-constants-javascript.md)   
 [JavaScript 常量](../../javascript/reference/javascript-constants.md)   
 [Infinity 常数](../../javascript/reference/infinity-constant-javascript.md)   
 [NaN 常量](../../javascript/reference/nan-constant-javascript.md)   
 [isNaN 函数](../../javascript/reference/isnan-function-javascript.md)