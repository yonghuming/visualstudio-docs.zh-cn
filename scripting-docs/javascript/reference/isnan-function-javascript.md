---
title: "isNaN 函数 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "isNaN"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "isNaN 方法"
ms.assetid: 5af4eb29-72f6-484f-93bd-04ae1261f849
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# isNaN 函数 (JavaScript)
返回一个布尔值，该值指示某值是否为保留值 `NaN`（非数字）。  
  
## 语法  
  
```  
isNaN(numValue)   
```  
  
## 返回值  
 如果转换为 `Number` 类型的值为 `NaN`，则为 `true`，否则为 `false`。  
  
## 备注  
 必需的 `numValue` 是要针对 `NaN` 进行测试的值。  
  
 通常使用此方法来检测来自 `parseInt` 和 `parseFloat` 方法的返回值。  
  
 或者，可以将包含 `NaN` 或另一个值的变量与其自身进行比较。  如果比较的结果不相等，则该变量为 `NaN`。  因为 `NaN` 是唯一的一个与其自身不等的值。  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **应用于**：[Global 对象](../../javascript/reference/global-object-javascript.md)  
  
## 示例  
  
```javascript  
// Returns false.  
isNaN(100);  
  
// Returns false.  
isNaN("100");  
  
// Returns true.  
isNaN("ABC");  
  
// Returns true.  
isNaN("10C");  
  
// Returns true.  
isNaN("abc123");  
  
// Returns true.  
isNaN(Math.sqrt(-1));           
```  
  
## 请参阅  
 [isFinite 函数](../../javascript/reference/isfinite-function-javascript.md)   
 [NaN 常量](../../javascript/reference/nan-constant-javascript.md)   
 [parseFloat 函数](../../javascript/reference/parsefloat-function-javascript.md)   
 [parseInt 函数](../../javascript/reference/parseint-function-javascript.md)