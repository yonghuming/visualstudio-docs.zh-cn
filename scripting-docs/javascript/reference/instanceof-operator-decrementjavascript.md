---
title: "instanceof 运算符 (JavaScript) | Microsoft Docs"
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
  - "instanceof_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "instanceOf 运算符"
ms.assetid: 92467bdc-56b5-42dc-adbd-a219776454d2
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# instanceof 运算符 (JavaScript)
返回一个布尔值，该值指示一个对象是否为特定类的一个实例。  
  
## 语法  
  
```  
  
result = object instanceof class  
```  
  
## 参数  
 `result`  
 必需。  任何变量。  
  
 `object`  
 必需。  任何对象表达式。  
  
 `class`  
 必需。  任何定义的对象类。  
  
## 备注  
 如果 `object` 是 `class` 的一个实例，则 `instanceof` 运算符返回 `true`。  如果 `class` 存在于对象的原型链中（为 `true`），则该运算符返回 `true`。  如果 `object` 不是 `class` 的实例，或 `object` 为 `null`，则该运算符返回 `false`。  
  
## 示例  
 以下示例演示如何使用 `instanceof` 运算符。  
  
```javascript  
function objTest(obj){  
    var i, t, s = "";  
    t = new Array();  
    t["Date"] = Date;  
    t["Object"] = Object;  
    t["Array"] = Array;  
        for (i in t){  
            if (obj instanceof t[i]) {   
                s += "obj is an instance of " + i + "<br/>";  
            }  
            else {  
                s += "obj is not an instance of " + i + "<br/>";  
        }  
    }  
    return(s);  
}  
  
var obj = new Date();  
document.write(objTest(obj));  
  
// Output:   
// obj is an instance of Date  
// obj is an instance of Object  
// obj is not an instance of Array  
```  
  
## 要求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## 请参阅  
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)