---
title: "startsWith 方法（字符串）(JavaScript) | Microsoft Docs"
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
ms.assetid: 871def4a-0f96-4675-b6ff-2349f4996511
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# startsWith 方法（字符串）(JavaScript)
返回一个值，该值指示字符串或子字符串是否以另一个指定字符串开头。  
  
## 语法  
  
```vb  
  
stringObj.startsWith(str, [, position]);  
```  
  
#### 参数  
 `stringObj`  
 必需。  要搜索的字符串对象。  
  
 `str`  
 必需。  搜索字符串。  
  
 `position`  
 可选。  字符串对象中要搜索的以 0 开头的第一个字符的位置。  
  
## 返回值  
 如果以 `position` 开始的字符串以搜索字符串开头，则 `startsWith` 方法返回 `true`；否则返回 `false`。  
  
## 异常  
 如果 `str` 为 `RegExp`，则引发 `TypeError`。  
  
## 备注  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]