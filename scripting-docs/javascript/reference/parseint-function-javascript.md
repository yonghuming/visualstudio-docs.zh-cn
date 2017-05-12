---
title: "parseInt 函数 (JavaScript) | Microsoft Docs"
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
  - "parseInt"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "parseInt 方法"
ms.assetid: e86471af-2a0e-4359-83af-f1ac81e51421
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# parseInt 函数 (JavaScript)
将字符串转换为整数。  
  
## 语法  
  
```  
parseInt(numString, [radix])   
```  
  
## 参数  
 `numString`  
 必需。  要转换为数字的字符串。  
  
 `radix`  
 可选。  一个介于 2 和 36 之间的值，用于指定 `numString` 所包含的数字的进制。  如果未提供此参数，则前缀为“0x”的字符串将被视为是十六进制。  所有其他字符串都被视为是十进制。  
  
## 备注  
 `parseInt` 函数返回一个等于 `numString` 中包含的数字的整数值。  如果没有 `numString` 的前缀可以被成功地分析为一个整数，则返回 `NaN`（非数字）。  
  
```javascript  
parseInt("abc");     // Returns NaN.  
parseInt("12abc");   // Returns 12.  
```  
  
 可使用 `isNaN` 函数测试是否为 `NaN`。  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**：[Global 对象](../../javascript/reference/global-object-javascript.md)  
  
> [!NOTE]
>  从 [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)] 中开始，`parseInt` 函数不将前缀为“0”的字符串视作八进制。  但在不使用 `parseInt` 函数时，前缀为“0”的字符串仍可被解释为八进制。  有关八进制整数的信息，请参见[数据类型](../../javascript/data-types-javascript.md)。  
  
## 请参阅  
 [isNaN 函数](../../javascript/reference/isnan-function-javascript.md)   
 [parseFloat 函数](../../javascript/reference/parsefloat-function-javascript.md)   
 [String 对象](../../javascript/reference/string-object-javascript.md)   
 [valueOf 方法 \(Object\)](../../javascript/reference/valueof-method-object-javascript.md)