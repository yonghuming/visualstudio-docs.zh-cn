---
title: "isFinite 函数 (JavaScript) | Microsoft Docs"
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
  - "isFinite"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "有限数字"
  - "isFinite 方法"
ms.assetid: ea9287d2-892f-496b-86b7-f9196868d5cf
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# isFinite 函数 (JavaScript)
确定所提供的数字是否是有限值。  
  
## 语法  
  
```  
isFinite(number)   
```  
  
## 备注  
 必需的 `number` 参数是任何数值。  
  
 如果 `number` 是除 `NaN`、负无穷或正无穷之外的任意值，则 `isFinite` 函数将返回 `true`。  在这三种情况中，函数返回 **false**。  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[Global 对象](../../javascript/reference/global-object-javascript.md)  
  
## 请参阅  
 [isNaN 函数](../../javascript/reference/isnan-function-javascript.md)