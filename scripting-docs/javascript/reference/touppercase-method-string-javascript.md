---
title: "toUpperCase 方法 (String) (JavaScript) | Microsoft Docs"
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
  - "toUpperCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toUpperCase 方法"
ms.assetid: 4fd4ccc3-e794-498a-9db1-baf48fc1dda1
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# toUpperCase 方法 (String) (JavaScript)
将字符串中的所有字母字符转换为大写形式。  
  
## 语法  
  
```  
  
        strVariable.toUpperCase()  
"String Literal".toUpperCase()   
```  
  
## 备注  
 `toUpperCase` 方法对非字母字符无效。  
  
## 示例  
 下面的示例说明了 `toUpperCase` 方法的效果：  
  
```javascript  
var str1 = "This is a STRING.";  
var str2 = str1.toUpperCase();  
document.write(str2);  
  
// Output: THIS IS A STRING.  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **应用于**：[String 对象](../../javascript/reference/string-object-javascript.md)  
  
## 请参阅  
 [toLocaleUpperCase 方法 \(String\)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [toLowerCase 方法](../../javascript/reference/tolowercase-method-javascript.md)