---
title: "stackTraceLimit 属性（错误）(JavaScript) | Microsoft Docs"
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
  - "Error.stackTraceLimit"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "错误堆栈跟踪限制 [JavaScript]"
  - "JavaScript 错误堆栈"
  - "错误堆栈 [JavaScript]"
  - "JavaScript 堆栈跟踪限制"
ms.assetid: 127ef8e8-892e-4263-9ebc-03364af01212
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# stackTraceLimit 属性（错误）(JavaScript)
获取或设置堆栈跟踪限制，它与要显示的错误帧数相等。  默认限制为 10。  
  
## 语法  
  
```  
  
Error  
.stackTraceLimit   
```  
  
## 备注  
 可以将 `stackTraceLimit` 属性设置为 0 到 `Infinity` 之间的任何正值。  如果在引发错误时将 `stackTraceLimit` 属性设置为 0，则不显示堆栈跟踪。  如果将该属性设置为负值或非数值，则该值转换为 0。  如果将 stackTraceLimit 设置为 `Infinity`，则显示整个堆栈。  否则，`ToUint32` 将用于转换该值。  
  
## 示例  
 以下示例演示了如何设置并获取堆栈跟踪限制。  
  
```javascript  
try  
    {  
    var err = new Error("my error");  
    Error.stackTraceLimit = 7;  
    throw err;  
    }  
catch(e)  
    {  
    document.write ("Error stack trace limit: ")  
    document.write (Error.stackTraceLimit);  
    }  
```  
  
## 要求  
 在 Internet Explorer 10 和 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] app 中受支持。  
  
 **应用于**：[Error 对象](../../javascript/reference/error-object-javascript.md)  
  
## 请参阅  
 [description 属性（错误）](../../javascript/reference/description-property-error-javascript.md)   
 [message 属性（错误）](../../javascript/reference/message-property-error-javascript.md)   
 [name 属性（错误）](../../javascript/reference/name-property-error-javascript.md)   
 [stack 属性（错误）](../../javascript/reference/stack-property-error-javascript.md)