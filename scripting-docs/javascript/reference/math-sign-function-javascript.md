---
title: "Math.sign 函数 (JavaScript) | Microsoft Docs"
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
ms.assetid: 8b462020-ceff-4947-8dd1-c78e6aff8d98
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Math.sign 函数 (JavaScript)
返回数字符号，它指示数字为正数、负数还是 0。  
  
## 语法  
  
```  
Math.sign(number)  
```  
  
## 备注  
 所需的 `number` 参数是一个需要符号的数值表达式。  
  
 返回值为下列之一：  
  
-   如果 `number` 是 `NaN`，则为 `NaN`。  
  
-   如果 `number` 是 −0，则为 \-0。  
  
-   如果 `number` 是 \+0，则为 \+0。  
  
-   如果 `number` 是负数且不为 −0，则为 \-1。  
  
-   如果 `number` 是正数且不为 \+0，则为 \+1。  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]