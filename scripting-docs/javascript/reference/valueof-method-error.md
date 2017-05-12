---
title: "valueOf 方法（错误） | Microsoft Docs"
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
ms.assetid: ca25c57d-c9ad-445b-8235-561390de680c
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# valueOf 方法（错误）
返回错误的字符串值。  
  
## 语法  
  
```  
  
error.valueOf()  
```  
  
#### 参数  
 `error` 对象是 Error 的任何实例。  
  
## 返回值  
 字符串“Error:”以及错误消息。  
  
## 示例  
 下面的示例阐释了使用日期的 `valueOF` 方法的用法。  
  
```javascript  
var myError = new Error();  
myError.message = "This is an error.";  
var value = myError.valueOf();  
document.write(value);  
  
// Output: Error: This is an error.  
  
```  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]