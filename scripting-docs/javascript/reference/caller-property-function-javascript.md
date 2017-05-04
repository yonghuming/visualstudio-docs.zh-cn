---
title: "caller 属性（函数）(JavaScript) | Microsoft Docs"
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
  - "caller"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "caller 属性"
  - "函数调用，正在执行的函数"
ms.assetid: ae210853-7160-4102-9cfd-ab489f180ce1
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# caller 属性（函数）(JavaScript)
获取调用当前函数的函数。  
  
## 语法  
  
```  
  
functionName.caller  
```  
  
## 备注  
 `functionName` 对象是任何正在执行的函数的名称。  
  
 `caller` 属性只有当函数正在执行时才被定义。  如果函数是从 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 程序的顶层调用的，则 `caller` 包含 `null`。  
  
 如果在字符串上下文中使用 `caller` 属性，则其结果和 `functionName`.`toString` 相同，也就是说，将显示函数的反编译文本。  
  
 下面的示例阐释了 `caller` 属性的用法：  
  
```javascript  
function CallLevel(){  
   if (CallLevel.caller == null)  
      return("CallLevel was called from the top level.");  
   else  
      return("CallLevel was called by another function.");  
}  
  
document.write(CallLevel());  
  
// Output: CallLevel was called from the top level.  
```  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## 请参阅  
 [function 语句](../../javascript/reference/function-statement-javascript.md)