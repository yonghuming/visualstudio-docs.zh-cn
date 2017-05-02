---
title: "constructor 属性（错误） | Microsoft Docs"
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
ms.assetid: 18aea278-2bd5-457b-83a5-d8d8f1226e0c
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor 属性（错误）
指定创建 Error 的函数。  
  
## 语法  
  
```  
  
error.constructor  
```  
  
## 备注  
 必需的 `error` 是一个 error 对象的名称。  
  
 `constructor` 属性是每个具有原型的对象的原型成员。  `constructor` 属性包含了对某种函数的引用，此种函数构造了特定对象的实例。  
  
## 示例  
 下面的示例阐释了 constructor 属性的用法。  
  
```javascript  
var x = new Error("This is an error");  
  
if (x.constructor == Error)  
    document.write("Object is an error.");  
  
// Output:  
// Object is an error.  
  
```  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]