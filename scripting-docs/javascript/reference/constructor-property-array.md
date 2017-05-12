---
title: "constructor 属性（数组） | Microsoft Docs"
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
ms.assetid: b78d517b-cb56-4866-b30f-ef8121a27843
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor 属性（数组）
指定创建一个数组的函数。  
  
## 语法  
  
```  
  
array.constructor  
```  
  
## 备注  
 必需的 `array` 是一个数组的名称。  
  
 `constructor` 属性是每个具有原型的对象的原型成员。  这包括除 `Global` 和 `Math` 对象之外的所有内部 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 对象。  `constructor` 属性包含了对某种函数的引用，此种函数构造了特定对象的实例。  
  
## 示例  
 下面的示例阐释了 constructor 属性的用法。  
  
```javascript  
var x = new Array();  
  
if (x.constructor == Array)  
    document.write("Object is an Array.");  
else  
    document.write("Object is not an Array.");  
  
// Output:  
// Object is an Array.  
  
```  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]