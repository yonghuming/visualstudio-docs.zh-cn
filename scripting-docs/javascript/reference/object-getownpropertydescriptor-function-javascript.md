---
title: "Object.getOwnPropertyDescriptor 函数 (JavaScript) | Microsoft Docs"
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
  - "getOwnPropertyDescriptor 方法 [JavaScript]"
ms.assetid: 8f0e1c90-c4f9-44c4-bf76-726bacecbc14
caps.latest.revision: 45
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 45
---
# Object.getOwnPropertyDescriptor 函数 (JavaScript)
获取指定对象的自身属性描述符。  自身属性描述符是指直接在对象上定义（而非从对象的原型继承）的描述符。  
  
## 语法  
  
```  
Object.getOwnPropertyDescriptor(object, propertyname)  
```  
  
## 参数  
 `object`  
 必需。  包含属性的对象。  
  
 `propertyname`  
 必需。  属性的名称。  
  
## 返回值  
 属性的描述符。  
  
## 备注  
 可以使用 `Object.getOwnPropertyDescriptor` 函数来获取描述属性特性的描述符对象。  
  
 [Object.defineProperty 函数](../../javascript/reference/object-defineproperty-function-javascript.md) 用于添加或修改属性。  
  
## 数据属性示例  
 以下示例获取数据属性描述符，并用它将属性设为只读。  
  
```javascript  
// Create a user-defined object.  
var obj = {};  
  
// Add a data property.  
obj.newDataProperty = "abc";  
  
// Get the property descriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
  
// Change a property attribute.  
descriptor.writable = false;  
Object.defineProperty(obj, "newDataProperty", descriptor);  
  
```  
  
 若要列出属性特性，可将以下代码添加到此示例中。  
  
```javascript  
// Get the descriptor from the object.  
var desc2 = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
  
// List the descriptor attributes.  
for (var prop in desc2) {  
    document.write(prop + ': ' + desc2[prop]);  
    document.write("<br />");  
}  
  
// Output:  
// value: abc  
// writable: false  
// enumerable: true  
// configurable: true  
```  
  
## 要求  
 [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] 中支持所有功能。  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)] 支持 DOM 对象，但不支持用户定义的对象。  可以指定 `enumerable` 和 `configurable` 特性，但不使用它们。  
  
## 请参阅  
 [文档对象模型原型，第 2 部分：访问器 \(getter\/setter\) 支持](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Object.defineProperty 函数](../../javascript/reference/object-defineproperty-function-javascript.md)