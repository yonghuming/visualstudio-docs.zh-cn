---
title: "typeof 运算符 (JavaScript) | Microsoft Docs"
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
  - "typeof_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "typeof 运算符"
ms.assetid: ee8a1036-119f-486f-b034-b07bdba87f0c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# typeof 运算符 (JavaScript)
返回一个用于标识表达式的数据类型的字符串。  
  
## 语法  
  
```  
  
typeof[(]expression[)] ;  
```  
  
## 备注  
 *expression* 参数是其搜索类型信息的任何表达式。  
  
 `typeof` 运算符把类型信息以字符串形式返回。  `typeof` 返回六种可能的值：“数字”、“字符串”、“布尔值”、“对象”、“函数”和“未定义”。  
  
 `typeof` 语法中的圆括号是可选的。  
  
## 示例  
 以下示例测试变量的数据类型。  
  
```javascript  
var index = 5;  
var result = (typeof index === 'number');  
// Output: true  
  
var description = "abc";  
var result = (typeof description === 'string');  
// Output: true  
```  
  
## 示例  
 以下示例为声明的和未声明的变量测试 `undefined` 的数据类型。  
  
```javascript  
var declared;  
var result = (declared === undefined);  
// Output: true  
  
var result = (typeof declared === 'undefined');  
// Output: true  
  
var result = (typeof notDeclared === 'undefined')  
// Output: true  
  
var obj = {};  
var result = (typeof obj.propNotDeclared === 'undefined');  
// Output: true  
  
// An undeclared variable cannot be used in a comparison without  
// the typeof operator, so the next line generates an error.  
//  var result = (notDeclared === undefined);  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [Array.isArray 函数](../../javascript/reference/array-isarray-function-javascript.md)   
 [Object.getPrototypeOf 函数](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [undefined 常量](../../javascript/reference/undefined-constant-javascript.md)   
 [比较运算符](../../javascript/reference/comparison-operators-javascript.md)   
 [数据类型](../../javascript/data-types-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)