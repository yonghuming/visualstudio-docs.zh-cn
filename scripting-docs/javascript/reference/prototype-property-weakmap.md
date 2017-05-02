---
title: "prototype 属性 (WeakMap) | Microsoft Docs"
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
ms.assetid: d28b8a9b-38c9-443d-9586-7cc74784bd99
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype 属性 (WeakMap)
为 `WeakMap` 对象返回对原型的引用。  
  
## 语法  
  
```javascript  
weakmap.prototype  
```  
  
## 备注  
 `weakmap` 参数是 `WeakMap` 对象的名称。  
  
 用 `prototype` 属性为对象的类提供一组基本功能。  对象的新的实例“继承”了赋予该对象的原型的行为。  
  
 例如，若要将方法添加到返回 `WeakMap` 的最大元素的值的 `WeakMap` 对象，请声明函数、将它添加到 `WeakMap.prototype` 并使用它。  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]