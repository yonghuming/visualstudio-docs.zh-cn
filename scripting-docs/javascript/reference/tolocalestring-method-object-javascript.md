---
title: "toLocaleString 方法 (Object) (JavaScript) | Microsoft Docs"
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
  - "toLocaleString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleString 方法"
ms.assetid: 0901afcb-126b-4ed7-bd6a-2301d50e2326
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toLocaleString 方法 (Object) (JavaScript)
返回使用当前区域设置转换为字符串的日期。  
  
## 语法  
  
```  
  
dateObj.toLocaleString()   
```  
  
## 备注  
 所需的 `dateObj` 是任意 `Date` 对象。  
  
 `toLocaleString` 方法返回一个 `String` 对象，此对象包含以当前区域设置的长默认格式编写的日期。  
  
-   对于公元 1601 和 1999 之间的日期，其格式将根据用户在“控制面板”中选择的“区域设置”确定。  
  
-   对于此范围之外的日期，将使用 **toString** 方法的默认格式。  
  
 例如，在美国，`toLocaleString` 为 1 月 5 日返回“01\/05\/96 00:00:00”。  在欧洲，它将为同一日期返回“05\/01\/96 00:00:00”，因为欧洲惯例是将日置于月份之前。  
  
> [!NOTE]
>  `toLocaleString` 应当仅用于向用户显示结果；决不可将它用作脚本中计算的基础，因为返回的结果因计算机而异。  
  
## 示例  
 下面的示例阐释了 `toLocaleString` 方法的用法。  
  
```javascript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**：[Array 对象](../../javascript/reference/array-object-javascript.md)&#124; [Date 对象](../../javascript/reference/date-object-javascript.md)&#124; [Number 对象](../../javascript/reference/number-object-javascript.md)&#124; [Object 对象](../../javascript/reference/object-object-javascript.md)  
  
## 请参阅  
 [toLocaleDateString 方法 \(Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)