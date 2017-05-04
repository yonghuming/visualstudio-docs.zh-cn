---
title: "undefined 常量 (JavaScript) | Microsoft Docs"
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
  - "undefined"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "undefined 属性"
ms.assetid: 2a689d7d-00b0-48fb-9c95-5c2867bde006
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# undefined 常量 (JavaScript)
一个从未定义的值，如未初始化的变量。  
  
## 语法  
  
```  
undefined  
```  
  
## 备注  
 `undefined` 常量是 `Global` 对象的一个成员，该常量在脚本引擎初始化后变得可用。  如果已声明了一个变量但还未进行初始化，则其值为 **undefined**。  
  
 如果还没有声明变量，则不能将其与 `undefined` 进行比较，但是可将变量的类型与字符串“undefined”进行比较。  
  
 当显式测试变量或将变量设置为未定义时，`undefined` 常量是很有用的。  
  
## 示例  
 下面的示例演示如何使用 `undefined` 常量。  
  
```javascript  
// A variable that has not been initialized.  
var declared;  
  
if (declared == undefined)  
    document.write("declared has not been given a value <br/>");  
else  
    document.write("declared has been given a value <br/>");  
  
document.write("typeof declared is " + typeof(declared) + "<br/>");  
  
// An undeclared variable cannot be compared to undefined,  
// so the next line would generate an error.  
// if (notDeclared == undefined);  
  
document.write("typeof notDeclared is " + typeof(notDeclared));  
  
// Output:  
// declared has not been given a value  
// typeof declared is undefined  
// typeof notDeclared is undefined  
```  
  
## 要求  
 `undefined` 属性已在 [!INCLUDE[jsv55text](../../javascript/reference/includes/jsv55text-md.md)] 中引入，并且在 [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)] 中已设置为只读。  
  
 **适用于**：[Global 对象](../../javascript/reference/global-object-javascript.md)  
  
## 请参阅  
 [typeof 运算符](../../javascript/reference/typeof-operator-decrementjavascript.md)