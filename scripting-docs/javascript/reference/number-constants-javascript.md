---
title: "Number 常量 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "常量 [JavaScript], 数字"
  - "MAX_VALUE 常量 [JavaScript]"
  - "MIN_VALUE 常量 [JavaScript]"
  - "NaN 常量 [JavaScript]"
  - "NEGATIVE_INFINITY 常量 [JavaScript]"
  - "number 常量 [JavaScript]"
  - "Number.MAX_VALUE 常量 [JavaScript]"
  - "Number.MIN_VALUE 常量 [JavaScript]"
  - "Number.NaN 常量 [JavaScript]"
  - "Number.NEGATIVE_INFINITY 常量 [JavaScript]"
  - "Number.POSITIVE_INFINITY 常量 [JavaScript]"
  - "POSITIVE_INFINITY 常量 [JavaScript]"
ms.assetid: e0701b41-99ae-4916-9ec0-f79bb15386fb
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Number 常量 (JavaScript)
以下数字常量是 `Number` 对象的属性。  
  
## Number 对象常量  
 您不必创建 `Number` 对象来访问这些常量。  
  
|返回的常量|值|  
|-----------|-------|  
|`Number.EPSILON`|可以在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中表示的最小数。  大约等于 2.2204460492503130808472633361816E\-16。|  
|`Number.MAX_SAFE_INTEGER`|可在 JavaScript 中安全表示的最大数。  等于 9007199254740991。|  
|`Number.MAX_VALUE`|可以在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中表示的最大数。  大约等于 1.79E\+308。|  
|`Number.MIN_SAFE_INTEGER`|可在 JavaScript 中安全表示的最小数。  等于 −9007199254740991。|  
|`Number.MIN_VALUE`|可以在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中表示的最接近零的数。  大约等于 5.00E\-324。|  
|`Number.NaN`|不是数字的值。<br /><br /> 在相等比较中，`NaN` 不等于任何值，包括它自身。  要测试该值是否与 `NaN` 等价，请使用 [isNaN 函数](../../javascript/reference/isnan-function-javascript.md)。|  
|`Number.NEGATIVE_INFINITY`|可以在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中表示的、小于最大负数的值。<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 将 `NEGATIVE_INFINITY` 值显示为 `-infinity`。|  
|`Number.POSITIVE_INFINITY`|可以在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中表示的、大于最大数的值。<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 将 `POSITIVE_INFINITY` 值显示为 `infinity`。|  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 对于 `Number.EPSILON`、`Number.MAX_SAFE_INTEGER` 和 `Number.MIN_SAFE_INTEGER`：  
  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **适用于**：[Number 对象](../../javascript/reference/number-object-javascript.md)  
  
## 请参阅  
 [Math 常量](../../javascript/reference/math-constants-javascript.md)   
 [JavaScript 常量](../../javascript/reference/javascript-constants.md)   
 [Infinity 常数](../../javascript/reference/infinity-constant-javascript.md)   
 [NaN 常量](../../javascript/reference/nan-constant-javascript.md)   
 [isNaN 函数](../../javascript/reference/isnan-function-javascript.md)