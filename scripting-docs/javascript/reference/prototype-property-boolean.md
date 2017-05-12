---
title: "prototype 属性（布尔值） | Microsoft Docs"
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
ms.assetid: e4f07cb5-3462-488c-a418-76064ab10eae
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype 属性（布尔值）
为布尔值返回对原型的引用。  
  
## 语法  
  
```  
  
boolean.prototype  
```  
  
## 备注  
 `boolean` 参数是对象的名称。  
  
 `prototype` 属性可为一类对象提供基础功能集。  对象的新实例“继承”了分配给该对象的原型的行为。  属性和方法可以添加至原型，但是可能无法为内置对象指定其他原型。  
  
 例如，要将方法添加到返回数组的最大元素值的 `Boolean` 对象，请声明该函数，将其添加至 `Boolean.prototype`，然后再使用它。  
  
```javascript  
function isFalse( ){  
    if (this.toString() == "false")  
         return true;  
    else  
        return false;  
}  
Boolean.prototype.isFalse = isFalse;  
var bool = new Boolean(1);  
document.write(bool.isFalse());  
  
// Output:  
// false  
  
```  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]