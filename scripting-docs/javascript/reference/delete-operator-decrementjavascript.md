---
title: "delete 运算符 (JavaScript) | Microsoft Docs"
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
  - "delete_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "数组元素，删除"
  - "属性，删除"
  - "delete 运算符"
ms.assetid: 55c6487e-96ea-455b-a7ed-dc35c41ac2f3
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# delete 运算符 (JavaScript)
从对象中删除一个属性，或从数组中移除一个元素。  
  
## 语法  
  
```  
delete expression  
```  
  
## 备注  
 `expression` 参数是有效的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 表达式，它通常生成属性名或数组元素。  
  
 如果 `expression` 的结果是一个对象，且在 `expression` 中指定的属性存在，同时该对象不允许此属性被删除，则将返回 `false`。  
  
 在所有其他情况下，将返回 `true`。  
  
## 示例  
 下面的示例演示如何从数组中移除元素。  
  
```javascript  
// Create an array.  
var ar = new Array (10, 11, 12, 13, 14);  
  
// Remove an element from the array.  
delete ar[1];  
  
// Print the results.  
document.write ("element 1: " + ar[1]);  
document.write ("<br />");  
document.write ("array: " + ar);  
// Output:  
//  element 1: undefined  
//  array: 10,,12,13,14  
```  
  
## 示例  
 下面的示例演示如何从某一对象删除属性。  
  
```javascript  
// Create an object and add expando properties.  
var myObj = new Object();  
myObj.name = "Fred";  
myObj.count = 42;  
  
// Delete the properties from the object.  
delete myObj.name;  
delete myObj["count"];  
  
// Print the results.  
document.write ("name: " + myObj.name);  
document.write ("<br />");  
document.write ("count: " + myObj.count);  
// Output:  
//  name: undefined  
//  count: undefined  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 请参阅  
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)