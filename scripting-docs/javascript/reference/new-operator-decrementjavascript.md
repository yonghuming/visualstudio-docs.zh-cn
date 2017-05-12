---
title: "new 运算符 (JavaScript) | Microsoft Docs"
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
  - "new_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JavaScript 中的 new 运算符"
ms.assetid: 5ea556ba-7ae6-426c-8430-9032eee5a0a5
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# new 运算符 (JavaScript)
创建一个新对象。  
  
## 语法  
  
```  
new constructor ([arguments])   
```  
  
## 参数  
 `constructor`  
 必需。  对象的构造函数。  若构造函数没有参数，则可省略圆括号。  
  
 `arguments`  
 可选。  任意传递给新对象的构造函数的参数。  
  
## 备注  
 `new` 运算符执行下列任务：  
  
-   创建一个没有成员的对象。  
  
-   它为该对象调用构造函数，并将一个指针作为 `this` 指针传递给新创建的对象。  
  
-   然后，构造函数根据传递给它的参数初始化该对象。  
  
 这些是 **new** 运算符的有效用法的示例。  
  
```javascript  
my_object = new Object;  
my_array = new Array();  
my_date = new Date("Jan 5 1996");  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [function 语句](../../javascript/reference/function-statement-javascript.md)