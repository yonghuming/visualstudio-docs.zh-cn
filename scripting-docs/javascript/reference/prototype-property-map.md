---
title: "prototype 属性 (Map) | Microsoft Docs"
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
ms.assetid: c7b429cb-97b7-400e-a214-1b18bddd6b02
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype 属性 (Map)
为映射返回对原型的引用。  
  
## 语法  
  
```javascript  
map.prototype  
```  
  
## 备注  
 `map` 参数是映射的名称。  
  
 用 `prototype` 属性为对象的类提供一组基本功能。  对象的新的实例“继承”了赋予该对象的原型的行为。  
  
 例如，若要将方法添加到返回集合的最大元素的值的 `Map` 对象，请声明函数、将它添加到 `Map.prototype` 并使用它。  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]