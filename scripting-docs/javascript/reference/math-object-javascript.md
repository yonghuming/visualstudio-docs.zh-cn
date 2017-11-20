---
title: "Math 对象 (JavaScript) |Microsoft 文档"
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
helpviewer_keywords: Math object
ms.assetid: 607b94cb-921c-43cd-b514-fdbc13aeced6
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f16fe4edf6a2a49db15d74abc8ebe6e53f955710
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="math-object-javascript"></a>Math 对象 (JavaScript)
提供基本数学功能和常量的内部对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
Math.[{property | method}]  
```  
  
## <a name="parameters"></a>参数  
 *属性*  
 必需。 其中一个的属性的名称**数学**。 的名称。  
  
 *方法*  
 必需。 名称的方法之一的**数学**。 的名称。  
  
## <a name="remarks"></a>备注  
 **数学**对象不能使用创建**新**运算符，并且如果你尝试执行此操作产生错误。 加载脚本引擎时，该引擎将创建它。 其所有方法和属性始终对你的脚本可用。  
  
## <a name="requirements"></a>要求  
 `Math` 中已引入 [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)] 对象。  
  
<a name="js56jsobjmathprop"></a>   
## <a name="constants"></a>常量  
 下表列出了 `Math` 对象的常量。  
  
|常量|描述|  
|--------------|-----------------|  
|[Math.E 常量](../../javascript/reference/math-constants-javascript.md)|数学常数 e。 这是欧拉数，自然对数的底。|  
|[Math.LN2 常量](../../javascript/reference/math-constants-javascript.md)|2 的自然对数。|  
|[Math.LN10 常量](../../javascript/reference/math-constants-javascript.md)|10 的自然对数。|  
|[Math.LOG2E 常量](../../javascript/reference/math-constants-javascript.md)|以 2 为底 e 的对数。|  
|[Math.LOG10E 常量](../../javascript/reference/math-constants-javascript.md)|以 10 为底 e 的对数。|  
|[Math.PI 常量](../../javascript/reference/math-constants-javascript.md)|Pi。 这是圆的周长与直径的比值。|  
|[Math.SQRT1_2 常量](../../javascript/reference/math-constants-javascript.md)|0.5 的平方根，或相当于 1 除以 2 的平方根。|  
|[Math.SQRT2 常量](../../javascript/reference/math-constants-javascript.md)|2 的平方根。|  
  
<a name="js56jsobjmathmeth"></a>   
## <a name="functions"></a>函数  
 下表列出了 `Math` 对象的函数。  
  
|函数|描述|  
|--------------|-----------------|  
|[Math.abs 函数](../../javascript/reference/math-abs-function-javascript.md)|返回数字的绝对值。|  
|[Math.acos 函数](../../javascript/reference/math-acos-function-javascript.md)|返回数字的反余弦值。|  
|[Math.acosh 函数](../../javascript/reference/math-acosh-function-javascript.md)|返回数字的双曲反余弦值（或反双曲余弦值）。|  
|[Math.asin 函数](../../javascript/reference/math-asin-function-javascript.md)|返回数字的反正弦值。|  
|[Math.asinh 函数](../../javascript/reference/math-asinh-function-javascript.md)|返回数字的反双曲正弦。|  
|[Math.atan 函数](../../javascript/reference/math-atan-function-javascript.md)|返回数字的反正切值。|  
|[Math.atan2 函数](../../javascript/reference/math-atan2-function-javascript.md)|将与 X 轴的角度（以弧度为单位）返回到由 y 和 x 坐标表示的点。|  
|[Math.atanh 函数](../../javascript/reference/math-atanh-function-javascript.md)|返回数字的反双曲正切。|  
|[Math.ceil 函数](../../javascript/reference/math-ceil-function-javascript.md)|返回大于或等于提供的数值表达式的最小整数。|  
|[Math.cos 函数](../../javascript/reference/math-cos-function-javascript.md)|返回数字的余弦值。|  
|[Math.cosh 函数](../../javascript/reference/math-cosh-function-javascript.md)|返回数字的双曲余弦。|  
|[Math.exp 函数](../../javascript/reference/math-exp-function-javascript.md)|返回*e* （自然对数的底） 乘幂。|  
|[Math.expm1 函数](../../javascript/reference/math-expm1-function-javascript.md)|返回 e（自然对数的底）的乘幂数减去 1 的结果。|  
|[Math.floor 函数](../../javascript/reference/math-floor-function-javascript.md)|返回小于或等于提供的数值表达式的最大整数。|  
|[Math.hypot 函数](../../javascript/reference/math-hypot-function-javascript.md)|返回自变量平方和的平方根。|  
|[Math.imul 函数](../../javascript/reference/math-imul-function-javascript.md)|返回被视为 32 位带符号整数的两个数字的积。|  
|[Math.log 函数](../../javascript/reference/math-log-function-javascript.md)|返回数字的自然对数。|  
|[Math.log1p 函数](../../javascript/reference/math-log1p-function-javascript.md)|返回 1 加上一个数字的的自然对数。|  
|[Math.log10 函数](../../javascript/reference/math-log10-function-javascript.md)|返回数字以 10 为底的对数。|  
|[Math.log2 函数](../../javascript/reference/math-log2-function-javascript.md)|返回数字以 2 为底的对数。|  
|[Math.max 函数](../../javascript/reference/math-max-function-javascript.md)|返回提供的两个数值表达式中的较大值。|  
|[Math.min 函数](../../javascript/reference/math-min-function-javascript.md)|返回提供的两个数字中的较小值。|  
|[Math.pow 函数](../../javascript/reference/math-pow-function-javascript.md)|返回基表达式的指定乘幂数的值。|  
|[Math.random 函数](../../javascript/reference/math-random-function-javascript.md)|返回介于 0 和 1 之间的伪随机数。|  
|[Math.round 函数](../../javascript/reference/math-round-function-javascript.md)|返回舍入到最近整数的指定数值表达式。|  
|[Math.sign 函数](../../javascript/reference/math-sign-function-javascript.md)|返回数字符号，它指示数字为正数、负数还是 0。|  
|[Math.sin 函数](../../javascript/reference/math-sin-function-javascript.md)|返回数字的正弦值。|  
|[Math.sinh 函数](../../javascript/reference/math-sinh-function-javascript.md)|返回数字的反双曲正弦。|  
|[Math.sqrt 函数](../../javascript/reference/math-sqrt-function-javascript.md)|返回数字的平方根。|  
|[Math.tan 函数](../../javascript/reference/math-tan-function-javascript.md)|返回数字的正切值。|  
|[Math.tanh 函数](../../javascript/reference/math-tanh-function-javascript.md)|返回数字的双曲正切。|  
|[Math.trunc 函数](../../javascript/reference/math-trunc-function-javascript.md)|返回数字的整数部分，删除任何小数数字。|  
  
## <a name="see-also"></a>另请参阅  
 [JavaScript 对象](../../javascript/reference/javascript-objects.md)   
 [Number 对象](../../javascript/reference/number-object-javascript.md)