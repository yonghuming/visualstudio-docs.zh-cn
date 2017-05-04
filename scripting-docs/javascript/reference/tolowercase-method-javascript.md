---
title: "toLowerCase 方法 (JavaScript) | Microsoft Docs"
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
  - "toLowerCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLowerCase 方法"
ms.assetid: dfd543b9-3e7a-4f83-a391-9cde109ad6bc
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# toLowerCase 方法 (JavaScript)
将字符串中的所有字母字符转换为小写形式。  
  
## 语法  
  
```  
  
        strVariable.toLowerCase()  
"String Literal".toLowerCase()   
```  
  
## 备注  
 `toLowerCase` 方法对非字母字符无效。  
  
 下面的示例说明了 `toLowerCase` 方法的效果：  
  
```javascript  
var str1 = "This is a STRING.";  
var str2 = str1. toLowerCase();  
document.write(str2);  
  
// Output: this is a string.  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **应用于**：[String 对象](../../javascript/reference/string-object-javascript.md)  
  
## 请参阅  
 [toLocaleLowerCase 方法 \(String\)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [toUpperCase 方法 \(String\)](../../javascript/reference/touppercase-method-string-javascript.md)