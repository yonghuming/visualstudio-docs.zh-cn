---
title: "Number 对象 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Number_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Number object
ms.assetid: 76e87c37-cf6c-46cc-bafa-04be1fe3d78d
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7cbe58fdc9673a8fffe35b8b15d7edbf86ffa655
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="number-object-javascript"></a>Number 对象 (JavaScript)
一个表示任何类型的数字的对象。 所有 JavaScript 数字均为 64 位浮点数。  
  
## <a name="syntax"></a>语法  
  
```  
  
numObj = new Number(value)  
```  
  
## <a name="parameters"></a>参数  
 `numObj`  
 必需。 `Number` 对象分配到的变量名称。  
  
 `value`  
 必需。 数值。  
  
## <a name="remarks"></a>备注  
 变量设置为数值（例如 `var num = 255.336;`）时，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 创建 `Number` 对象。 很少需要显式创建 `Number` 对象。  
  
 除了从 `Object` 继承的属性和方法，`Number` 对象自身还具有属性和方法。 在某些情况下，数字将转换为字符串，例如在向字符串添加或串联数字时，以及在使用 `toString` 方法执行这些操作时。 有关详细信息，请参阅[加法运算符 （+）](../../javascript/reference/addition-operator-decrement-javascript.md)。  
  
 JavaScript 具有多个数字常量。 完整列表，请参阅[数字常量](../../javascript/reference/number-constants-javascript.md)。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="properties"></a>属性  
 下表列出了 `Number` 对象的属性。  
  
|属性|描述|  
|--------------|-----------------|  
|[constructor 属性](../../javascript/reference/constructor-property-object-javascript.md)|指定用于创建对象的函数。|  
|[prototype 属性](../../javascript/reference/prototype-property-object-javascript.md)|为对象的类返回原型的引用。|  
  
## <a name="functions"></a>函数  
 下表列出的函数`Number`对象。  
  
|函数|描述|  
|--------------|-----------------|  
|[Number.isFinite 函数](../../javascript/reference/number-isfinite-function-number-javascript.md)|返回一个布尔值，该值指示值是否为有限数。|  
|[Number.isInteger 函数](../../javascript/reference/number-isinteger-function-number-javascript.md)|返回一个布尔值，该值指示值是否为整数。|  
|[Number.isNaN 函数](../../javascript/reference/number-isnan-function-number-javascript.md)|返回一个布尔值，该值指示某个值是否为保留值 `NaN`（非数字）。|  
|[Number.isSafeInteger](../../javascript/reference/number-issafeinteger-number-javascript.md)|返回一个布尔值，该值指示值是否可在 JavaScript 中安全表示。|  
  
## <a name="methods"></a>方法  
 下表列出的方法`Number`对象。  
  
|方法|描述|  
|------------|-----------------|  
|[hasOwnProperty 方法](../../javascript/reference/hasownproperty-method-object-javascript.md)|返回一个布尔值，该值指示某个对象是否具有指定名称的属性。|  
|[isPrototypeOf 方法](../../javascript/reference/isprototypeof-method-object-javascript.md)|返回一个布尔值，该值指示某个对象是否存在于另一个对象的原型层次结构中。|  
|[propertyIsEnumerable 方法](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|返回一个布尔值，该值指示指定属性是否为对象的一部分且是否可枚举。|  
|[toExponential 方法](../../javascript/reference/toexponential-method-number-javascript.md)|返回一个字符串，其中包含一个以指数记数法表示的数字。|  
|[toFixed 方法](../../javascript/reference/tofixed-method-number-javascript.md)|返回一个字符串，它表示定点表示法中的一个数字。|  
|[toLocaleString 方法](../../javascript/reference/tolocalestring-number.md)|返回基于当前区域设置转换为字符串的对象。|  
|[toPrecision 方法](../../javascript/reference/toprecision-method-number-javascript.md)|返回一个字符串，其中包含一个以指数或定点表示法表示且具有指定位数的数字。|  
|[toString 方法](../../javascript/reference/tostring-method-object-javascript.md)|返回对象的字符串表示形式。|  
|[valueOf 方法](../../javascript/reference/valueof-method-object-javascript.md)|返回指定对象的基元值。|  
  
## <a name="see-also"></a>另请参阅  
 [JavaScript 对象](../../javascript/reference/javascript-objects.md)   
 [Math 对象](../../javascript/reference/math-object-javascript.md)   
 [new 运算符](../../javascript/reference/new-operator-decrementjavascript.md)