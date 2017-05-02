---
title: "constructor 属性 (WeakMap) | Microsoft Docs"
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
ms.assetid: 1e3f9333-ce75-4d32-9b14-fbe81fd73dfb
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# constructor 属性 (WeakMap)
指定创建 `WeakMap` 对象的函数。  
  
## 语法  
  
```javascript  
weakmap.constructor  
```  
  
## 备注  
 所需的 `weakmap` 是 `WeakMap` 对象的名称。  
  
 `constructor` 属性是每个具有原型对象的原型成员。  这包括除 `Global` 和 `Math` 对象外的所有内部 JavaScript 对象。  `constructor` 属性包含了对某种函数的引用，此种函数构造了特定对象的实例。  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]