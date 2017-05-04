---
title: "propertyIsEnumerable 方法 (Object) (JavaScript) | Microsoft Docs"
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
  - "propertyIsEnumerable"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "propertyIsEnumerable 属性"
ms.assetid: d90c7c2e-ea23-4710-a957-9aefbbd1f68b
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# propertyIsEnumerable 方法 (Object) (JavaScript)
确定指定的属性是否可枚举。  
  
## 语法  
  
```  
  
object. propertyIsEnumerable(proName)  
```  
  
## 参数  
 `object`  
 必需。  对象的实例。  
  
 `proName`  
 必需。  一个属性名称的字符串值。  
  
## 备注  
 如果 `proName` 存在于 `object` 中，且可以使用 `For` 循环对其进行枚举，则 `propertyIsEnumerable` 方法返回 `true`。  如果 `object` 不具有所指定名称的属性或者所指定的属性是不可枚举的，则 `propertyIsEnumerable` 方法将返回 `false`。  通常，预定义的属性是不可枚举的，而用户定义的属性始终是可枚举的。  
  
 `propertyIsEnumerable` 方法不考虑原型链中的对象。  
  
## 示例  
  
```javascript  
var a = new Array("apple", "banana", "cactus");  
document.write(a.propertyIsEnumerable(1));  
  
// Output: true  
  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 请参阅  
 [prototype 属性（对象）](../../javascript/reference/prototype-property-object-javascript.md)