---
title: "constructor 属性（数字） | Microsoft Docs"
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
ms.assetid: a348fe53-1b4a-42f5-964b-53d57342c906
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor 属性（数字）
指定创建一个数字的函数。  
  
## 语法  
  
```  
  
number.constructor  
```  
  
## 备注  
 必需的 `number` 是字符串的名称。  
  
 `constructor` 属性是每个具有原型的对象的原型成员。  这包括除 `Global` 和 `Math` 对象之外的所有内部 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 对象。  `constructor` 属性包含了对某种函数的引用，此种函数构造了特定对象的实例。  
  
## 示例  
 下面的示例阐释了 constructor 属性的用法。  
  
```javascript  
var num = new Number();  
  
if (num.constructor == Number)  
    document.write("Object is a Number.");  
else  
    document.write("Object is not a Number.");  
  
// Output:  
// Object is a Number.  
  
```  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]