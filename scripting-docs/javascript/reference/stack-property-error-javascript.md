---
title: "stack 属性（错误）(JavaScript) | Microsoft Docs"
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
  - "Error.stack"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "错误堆栈 [JavaScript]"
  - "JavaScript 错误堆栈"
ms.assetid: 1dc21fdd-853c-4664-bf1c-24eb1f6f2daf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# stack 属性（错误）(JavaScript)
获取或设置作为包含堆栈跟踪帧的字符串的错误堆栈。  
  
## 语法  
  
```  
  
object  
.stack   
```  
  
## 备注  
 构造错误时，`stack` 属性设置为 `undefined`，并在引发该错误时获取跟踪信息。  如果多次引发某个错误，则 `stack` 属性将在每次引发该错误时更新。  
  
 堆栈帧的显示格式如下所示：位于 FunctionName \(\<完全限定名称\/URL\>:\<行号\>:\<列号\>\)  
  
 如果创建自己的 Error 对象并将堆栈跟踪设置为一个值，则在引发错误时，不会覆盖该值。  
  
 `stack` 属性不会在其帧中显示内联函数。  它只显示物理堆栈。  
  
## 示例  
 下面的示例演示如何在捕获错误时获取堆栈。  
  
```javascript  
try  
    {  
        var x = y.name;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## 示例  
 下面的示例演示如何设置并获取堆栈。  
  
```javascript  
try  
    {  
        var err = Error("my error");  
        err.stack = "my stack trace";  
        throw err;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## 要求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]  
  
 **适用于**：[Error 对象](../../javascript/reference/error-object-javascript.md)  
  
## 请参阅  
 [description 属性（错误）](../../javascript/reference/description-property-error-javascript.md)   
 [message 属性（错误）](../../javascript/reference/message-property-error-javascript.md)   
 [name 属性（错误）](../../javascript/reference/name-property-error-javascript.md)   
 [stackTraceLimit 属性（错误）](../../javascript/reference/stacktracelimit-property-error-javascript.md)