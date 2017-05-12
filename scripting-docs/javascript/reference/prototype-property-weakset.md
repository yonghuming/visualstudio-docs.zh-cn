---
title: "prototype 属性 (WeakSet) | Microsoft Docs"
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
ms.assetid: 950e15a2-2f56-4cb9-8e48-020efd97f938
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# prototype 属性 (WeakSet)
返回对 `WeakSet` 的原型的引用。  
  
## 语法  
  
```javascript  
weakset.prototype  
```  
  
## 备注  
 `weakset` 参数是集的名称。  
  
 使用 `prototype` 属性，从而向对象的类提供基本功能集。  对象的新实例“继承”了分配给该对象的原型的行为。  
  
 例如，要将方法添加到返回集的最大元素值的 `WeakSet` 对象，则声明该函数，将其添加至 `WeakSet.prototype`，然后再使用它。  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]