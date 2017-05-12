---
title: "includes 方法（字符串）(JavaScript) | Microsoft Docs"
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
ms.assetid: 2639e4e5-23ba-424a-80ea-be067a4cd65e
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# includes 方法（字符串）(JavaScript)
返回一个布尔值，该值指示传入字符串是否包含在字符串对象中。  
  
## 语法  
  
```  
stringObj.includes(substring [, position]);  
```  
  
#### 参数  
 `stringObj`  
 必需。  要测试的字符串对象。  
  
 `substring`  
 必需。  要测试的字符串。  
  
 `position`  
 可选。  字符串对象中要测试的以 0 开头的第一个字符的位置。  
  
## 返回值  
 如果传入的字符串包含在字符串对象中，则 `includes` 方法返回 `true`；否则返回 `false`。  
  
## 备注  
  
## 示例  
  
```javascript  
// Returns true   
"abcde".includes("cd")  
"abcde".includes("cd", 2)  
  
// Returns false  
"abcde".includes("CD")  
"abcde".includes("cd", 3)  
  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]