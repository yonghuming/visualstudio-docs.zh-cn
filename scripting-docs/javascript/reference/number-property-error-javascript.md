---
title: "number 属性（错误）(JavaScript) | Microsoft Docs"
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
  - "Number"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Number 属性"
ms.assetid: 8697e20b-a2b0-4e26-85c0-ab07ddfe8281
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# number 属性（错误）(JavaScript)
返回或设置与特定错误相关联的数字值。  `Error` 对象的默认属性是 **number**。  
  
## 语法  
  
```  
  
object  
.number [= errorNumber]  
```  
  
## 参数  
 *Object*  
 `Error` 对象的任意实例。  
  
 *errorNumber*  
 表示错误的整数。  
  
## 备注  
 错误号是一个 32 位的值。  较高的 16 位字是设施代码，而较低的字是错误代码。  若要确定错误代码，请使用 `&`（按位与）运算符来将 number 属性与十六进制数字 `0xFFFF` 组合。  
  
## 示例  
 下面的示例导致引发异常并显示从错误号派生的错误代码。  
  
```javascript  
try  
    {  
    // Cause an error.  
    var x = y;  
    }  
catch(e)  
    {  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
  
    document.write ("Facility Code: ")  
    document.write(e.number>>16 & 0x1FFF)  
    document.write ("<br />");  
  
    document.write ("Error Message: ")  
    document.write (e.message)  
    }  
```  
  
## 示例  
 此代码的输出如下所示。  
  
```javascript  
Error Code: 5009  
Facility Code: 10  
Error Message: 'y' is undefined  
```  
  
## 要求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **适用于**：[Error 对象](../../javascript/reference/error-object-javascript.md)  
  
## 请参阅  
 [description 属性（错误）](../../javascript/reference/description-property-error-javascript.md)   
 [message 属性（错误）](../../javascript/reference/message-property-error-javascript.md)   
 [name 属性（错误）](../../javascript/reference/name-property-error-javascript.md)