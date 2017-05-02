---
title: "isPrototypeOf 方法 (Object) (JavaScript) | Microsoft Docs"
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
  - "isPrototypeOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "isPrototypeOf 方法"
ms.assetid: 9c821319-c208-480f-915e-565ef6e017b6
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# isPrototypeOf 方法 (Object) (JavaScript)
确定一个对象是否存在于另一个对象的原型链中。  
  
## 语法  
  
```  
  
prototype.isPrototypeOf(object)  
```  
  
## 参数  
 `prototype`  
 必选。  对象原型。  
  
 `object`  
 必选。  另一个对象，将对其原型链进行检查。  
  
## 备注  
 如果 `object` 的原型链中具有 `prototype`，则 `isPrototypeOf` 方法返回 `true`。  原型链用于在同一个对象类型的不同实例之间共享功能。  当 `object` 不是对象或当 `prototype` 没有出现在 `object` 的原型链中时，`isPrototypeOf` 方法返回 `false`。  
  
## 示例  
 下面的示例演示 `isPrototypeOf` 方法的用法。  
  
```javascript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
document.write(Rectangle.prototype.isPrototypeOf(rec));  
  
// Output: true  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 请参阅  
 [prototype 属性（对象）](../../javascript/reference/prototype-property-object-javascript.md)