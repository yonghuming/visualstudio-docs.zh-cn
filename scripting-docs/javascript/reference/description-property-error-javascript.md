---
title: "description 属性（错误）(JavaScript) | Microsoft Docs"
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
  - "Description"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Description 属性"
  - "错误处理, 错误说明"
  - "错误, 描述"
ms.assetid: ea727f1e-2041-4400-965c-67e6d47a1ff0
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# description 属性（错误）(JavaScript)
返回或设置与特定错误相关联的描述性字符串。  
  
## 语法  
  
```  
  
object  
.description [= stringExpression]  
```  
  
## 参数  
 *object*  
 必需。  `Error` 对象的任何实例。  
  
 `stringExpression`  
 可选。  一个包含错误说明的字符串表达式。  
  
## 备注  
 **description** 属性包含与特定错误关联的错误消息字符串。  使用此属性中包含的值来告知用户错误。  
  
 **description** 和 **message** 属性提供相同的功能；**description** 属性提供向后兼容性；**message** 属性符合 ECMA 标准。  
  
## 示例  
 下面的示例阐释了 **description** 属性的用法。  
  
```javascript  
try  
{  
// Cause an error:  
    x = y     
}  
catch(e)  
{  
// Prints "[object Error]":  
    document.write(e)  
    document.write (" ");  
// Prints 5009:  
    document.write((e.number & 0xFFFF))    
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.description);  
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.message)  
}  
```  
  
## 要求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **适用于**：[Error 对象](../../javascript/reference/error-object-javascript.md)  
  
## 请参阅  
 [number 属性（错误）](../../javascript/reference/number-property-error-javascript.md)   
 [message 属性（错误）](../../javascript/reference/message-property-error-javascript.md)   
 [name 属性（错误）](../../javascript/reference/name-property-error-javascript.md)