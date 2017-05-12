---
title: "Number.isInteger 函数（数字）(JavaScript) | Microsoft Docs"
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
ms.assetid: 54fcf68c-0067-4bad-af94-d7ff8c88914a
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Number.isInteger 函数（数字）(JavaScript)
返回一个布尔值，该值指示值是否为整数。  
  
## 语法  
  
```  
Number.isInteger(numValue)   
```  
  
## 返回值  
 如果值为整数则为 `true`，否则为 `false`。  
  
## 备注  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **适用于**：[Number 对象](../../javascript/reference/number-object-javascript.md)  
  
## 示例  
  
```javascript  
// Returns true  
Number.isInteger(100)  
Number.isInteger(-100)  
  
// Returns false  
Number.isInteger(Number.NaN)  
Number.isInteger(Infinity)  
Number.isInteger(100 / 3)  
Number.isInteger("100")  
  
```