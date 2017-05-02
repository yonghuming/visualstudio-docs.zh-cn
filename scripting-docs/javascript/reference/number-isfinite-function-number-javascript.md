---
title: "Number.isFinite 函数（数字）(JavaScript) | Microsoft Docs"
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
ms.assetid: 41a91408-09d1-49f2-b7a0-6da105e2ed8e
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Number.isFinite 函数（数字）(JavaScript)
返回一个布尔值，该值指示值是否为有限数字。  
  
## 语法  
  
```  
Number.isFinite(numValue)   
```  
  
## 返回值  
 如果值为 `NaN``+∞` 或 `-∞`，则为 `false`；否则为 `true`。  
  
## 备注  
  
## 示例  
  
```javascript  
// Returns true  
Number.isFinite(100)  
Number.isFinite(-100)  
Number.isFinite(100 / 3)  
  
// Returns false  
Number.isFinite(Number.NaN)  
Number.isFinite(Infinity)  
Number.isFinite("100")  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **适用于**：[Number 对象](../../javascript/reference/number-object-javascript.md)