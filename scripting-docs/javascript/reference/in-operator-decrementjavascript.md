---
title: "in 运算符 (JavaScript) | Microsoft Docs"
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
  - "in_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "in 运算符"
ms.assetid: dcd8f901-96b8-4c91-848b-b1ec0ab1c11c
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# in 运算符 (JavaScript)
测试一个对象中是否存在一种属性。  
  
## 语法  
  
```  
  
result = property in object  
```  
  
## 参数  
 `result`  
 必需。  任何变量。  
  
 `property`  
 必需。  计算结果为字符串表达式的表达式。  
  
 `object`  
 必需。  任意对象。  
  
## 备注  
 `in` 运算符确定对象中是否有名为 `property` 的属性。  它还确定属性是否为对象的原型链的一部分。  有关对象原型的更多信息，请参见[原型和原型继承](../../javascript/advanced/prototypes-and-prototype-inheritance.md)。  
  
## 示例  
 下面的示例演示如何使用 `in` 运算符：  
  
```javascript  
// Create an object that has some properties.  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 0234";  
  
if ("phone" in myObject)  
   document.write ("property is present");  
else  
   document.write ("property is not present");  
  
// Output: property is present  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)