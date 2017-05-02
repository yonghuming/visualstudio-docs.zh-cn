---
title: "Math.clz32 函数 (JavaScript) | Microsoft Docs"
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
ms.assetid: 34615d7a-6d88-4ab5-a696-7e496caa51db
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Math.clz32 函数 (JavaScript)
返回数字的 32 位二进制表示形式中的前导零位数。  
  
## 语法  
  
```  
  
Math.clz32(  
number  
)   
```  
  
## 备注  
 如果 `number` 为 0，则结果将为 32。  如果 `number` 的 32 位二进制编码的最高有效位为 1，则结果将为 0。  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **适用于**：[Math 对象](../../javascript/reference/math-object-javascript.md)