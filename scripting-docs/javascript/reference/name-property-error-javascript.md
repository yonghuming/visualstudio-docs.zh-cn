---
title: "name 属性（错误）(JavaScript) | Microsoft Docs"
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
  - "name"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Name 属性"
  - "name 属性, 错误名称。"
ms.assetid: 94df2d6b-f1a1-4931-a956-0a930cb87f76
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# name 属性（错误）(JavaScript)
返回错误的名称。  
  
## 语法  
  
```  
  
errorObj.  
name  
  
```  
  
## 参数  
 `errorObj`  
 必需。  `Error` 对象的实例。  
  
## 备注  
 **name** 属性返回错误的名称或异常类型。  当发生运行时错误时，名称属性将被设置为下列本机异常类型之一：  
  
|异常类型|含义|  
|----------|--------|  
|ConversionError|每当尝试对一个对象进行它所无法完成的转换时，将发生此错误。|  
|RangeError|当给一个函数提供一个超过其允许范围的参数时，将发生此错误。  例如，当尝试构造的 `Array` 对象的长度不是有效的正整数时，发生此错误。|  
|ReferenceError|如果检测到无效引用，则出现此错误。  例如，如果所需的引用为 `null`，将发生此错误。|  
|RegExpError|当正则表达式产生编译错误时，将发生此错误。  然而，一旦该正则表达式经过了编译，就不会发生此错误。  例如，如果声明正则表达式的模式使用了无效的语法或使用了 **i**、**g** 或 **m** 以外的标志，或者多次包含同一个标志，将发生此错误。|  
|SyntaxError|当分析源文本后发现它不遵循正确的语法时，将发生此错误。  例如，当调用 `eval` 函数的参数不是有效的程序文本时，将发生此错误。|  
|TypeError|当操作数的实际类型与所期望的类型不符时，将发生此错误。  例如，如果在不是对象的内容上进行函数调用或者该内容不支持该调用时，发生此错误。|  
|URIError|在检测到非法的统一资源标识符 \(URI\) 时，会出现此错误。  例如，在正编码或解码的字符串中发现非法字符时，发生此错误。|  
  
## 示例  
 下面的示例导致引发了 TypeError 异常，并显示了错误名称及其消息。  
  
```javascript  
try  
{  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## 示例  
 此代码的输出如下所示。  
  
```javascript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**：[Error 对象](../../javascript/reference/error-object-javascript.md)  
  
## 请参阅  
 [description 属性（错误）](../../javascript/reference/description-property-error-javascript.md)   
 [message 属性（错误）](../../javascript/reference/message-property-error-javascript.md)   
 [number 属性（错误）](../../javascript/reference/number-property-error-javascript.md)