---
title: "Number.isNaN 函数（数字）(JavaScript) | Microsoft Docs"
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
ms.assetid: 2d9813d6-ec9c-433b-b060-8e3c3ff62ca4
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Number.isNaN 函数（数字）(JavaScript)
返回一个布尔值，该值指示某个值是否为保留值 `NaN`（非数字）。  
  
## 语法  
  
```  
Number.isNaN(numValue)   
```  
  
#### 参数  
 `numValue`  
 必需。  要针对 `NaN` 进行测试的值。  
  
## 返回值  
 如果转换为 `Number` 类型的值为 `NaN`，则为 `true`，否则为 `false`。  
  
## 备注  
 通常使用此方法来测试 `parseInt` 和 `parseFloat` 方法的返回值。  
  
 `Number.isNaN` 更正全局 `isNaN` 函数的问题。  `Number.isNaN` 仅在将其参数与 `NaN` 进行比较后将该参数转换为 Number 类型。  因此，当且仅当传入的参数与 `NaN` 的值完全相同时，它才返回 `true`。  全局 `isNaN` 函数在进行比较之前将其参数转换为 Number 类型，这可能会导致非数字值返回 `true`，而对于 `Number.isNaN`可能不会返回 `true`。  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **适用于**：[Number 对象](../../javascript/reference/number-object-javascript.md)  
  
## 示例  
  
```javascript  
// Returns true.  
Number.isNaN(NaN);  
Number.isNaN(Number.NaN);  
Number.isNaN(0 / 0);  
  
// Returns false.  
Number.isNaN(100);  
// Returns false.  
// Strings are converted to numbers and return false.  
Number.isNaN("100");  
Number.isNaN("ABC");  
Number.isNaN("10C");  
Number.isNaN("abc123");  
  
```