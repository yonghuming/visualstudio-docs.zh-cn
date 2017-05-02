---
title: "toLocaleUpperCase 方法 (String) (JavaScript) | Microsoft Docs"
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
  - "toLocaleUpperCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleUpperCase 方法"
ms.assetid: e927adb6-475e-44b2-91f7-cedda10a39b0
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# toLocaleUpperCase 方法 (String) (JavaScript)
返回一个字符串，其中所有字母字符都已转换为大写形式，并将考虑主机环境的当前区域设置。  
  
## 语法  
  
```  
  
stringVar.toLocaleUpperCase( )  
```  
  
## 备注  
 必需的 `stringVar` 引用是 `String` 对象或字符串。  
  
 `toLocaleUpperCase` 方法转换字符串中的字符，同时考虑到宿主环境的当前区域设置。  大多数情况下，此结果与使用 `toUpperCase` 方法所获得的结果相同。  如果语言规则与常规的 Unicode 大小写映射冲突，则结果将会不同。  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**：[String 对象](../../javascript/reference/string-object-javascript.md)  
  
## 请参阅  
 [toLocaleLowerCase 方法 \(String\)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [toUpperCase 方法 \(String\)](../../javascript/reference/touppercase-method-string-javascript.md)