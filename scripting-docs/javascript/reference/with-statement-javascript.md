---
title: "with 语句 (JavaScript) | Microsoft Docs"
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
  - "with_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "With 语句"
ms.assetid: 892c7621-ae9e-4c10-8adb-05532274b1ca
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# with 语句 (JavaScript)
为语句建立默认对象。  
  
## 语法  
  
```  
with (object) {  
    statements  
}   
```  
  
## 参数  
 `object`  
 默认对象。  
  
 `statements`  
 `object` 作为默认对象的一个或多个语句。  
  
## 备注  
 `with` 语句通常用来减少特定情形下必须写入的代码数量。  
  
> [!WARNING]
>  在严格模式中不允许使用 `with`。  使用 `with` 会导致代码更难读取和调试，因此通常应当避免。  
  
## 示例  
 在此示例中，`Math` 对象重复使用：  
  
```javascript  
x = Math.cos(3 * Math.PI) + Math.sin(Math.LN10)   
y = Math.tan(14 * Math.E)  
```  
  
## 示例  
 如果重写该示例以使用 `with` 语句，你的代码将变得更加简洁：  
  
```javascript  
with (Math){  
   x = cos(3 * PI) + sin (LN10)    
   y = tan(14 * E)  
}  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [this 语句](../../javascript/reference/this-statement-javascript.md)