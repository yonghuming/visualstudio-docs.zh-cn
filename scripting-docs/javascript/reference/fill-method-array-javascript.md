---
title: "fill 方法（数组）(JavaScript) | Microsoft Docs"
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
ms.assetid: 11526627-c0bb-4157-a8c4-0a039079b4a1
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# fill 方法（数组）(JavaScript)
使用指定值填充数组。  
  
## 语法  
  
```  
arrayObj.fill(value [ , start [ , end ] ]);  
```  
  
#### 参数  
 `arrayObj`  
 必需。  数组对象。  
  
 `value`  
 必需。  用于填充数组的值。  
  
 `start`  
 可选。  用于填充数组值的起始索引。  默认值为 0。  
  
 `end`  
 可选。  用于填充数组值的结束索引。  默认值是 `this` 对象的 length 属性。  
  
## 备注  
 如果 `start` 为负，则 `start` 被视为 `length`\+`start`，其中，`length` 是数组的长度。  如果 `end` 为负，则 `end` 被视为 `length`\+`end`。  
  
## 示例  
 以下代码示例用值填充数组。  
  
```javascript  
[0, 0, 0].fill(7, 1);  
// Array contains [0,7,7]  
  
[0, 0, 0].fill(7);  
// Array contains [7,7,7]  
  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]