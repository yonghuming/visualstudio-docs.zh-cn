---
title: "unshift 方法 (Array) (JavaScript) | Microsoft Docs"
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
  - "unshift"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "unshift 方法"
ms.assetid: 8c6a39ed-bab3-4ca4-9350-571a9427ec94
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# unshift 方法 (Array) (JavaScript)
在数组的开头插入新元素。  
  
## 语法  
  
```  
  
arrayObj.unshift([item1[, item2 [, . . . [, itemN]]]])  
```  
  
## 参数  
 `arrayObj`  
 必需。  一个 `Array` 对象。  
  
 `item1, item2,. . ., itemN`  
 可选。  用于插到 `Array` 开头的元素。  
  
## 备注  
 `unshift` 方法将这些元素插入到一个数组的开头，以便它们按其在参数表中的次序排列。  
  
## 示例  
 下面的示例阐释了 `unshift` 方法的用法。  
  
```javascript  
var ar = new Array();  
ar.unshift(10, 11);  
ar.unshift(12, 13, 14);  
document.write(ar.toString());  
  
// Output: 12,13,14,10,11  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 请参阅  
 [shift 方法 \(Array\)](../../javascript/reference/shift-method-array-javascript.md)