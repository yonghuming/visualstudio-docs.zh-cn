---
title: "toLocaleLowerCase 方法 (String) (JavaScript) | Microsoft Docs"
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
  - "toLocaleLowerCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleLowerCase 方法"
ms.assetid: add894d3-d14a-4dbc-a9b9-7ad1d3a2e581
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# toLocaleLowerCase 方法 (String) (JavaScript)
将所有字母字符都转换为小写形式，并考虑主机环境的当前区域设置。  
  
## 语法  
  
```  
  
stringVar.toLocaleLowerCase( )  
```  
  
## 备注  
 必需的 `stringVar` 引用是 `String` 对象或字符串。  
  
 `toLocaleLowerCase` 方法转换字符串中的字符，同时考虑到宿主环境的当前区域设置。  大多数情况下，此结果与使用 `toLowerCase` 方法所获得的结果相同。  如果语言规则与常规的 Unicode 大小写映射冲突，则结果将会不同。  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**：[String 对象](../../javascript/reference/string-object-javascript.md)  
  
## 请参阅  
 [toLocaleUpperCase 方法 \(String\)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [toLowerCase 方法](../../javascript/reference/tolowercase-method-javascript.md)