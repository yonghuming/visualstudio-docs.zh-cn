---
title: "message 属性（错误）(JavaScript) | Microsoft Docs"
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
  - "message"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Message 属性"
ms.assetid: 8cab0392-e0db-4714-827c-47ab04e8b4f2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# message 属性（错误）(JavaScript)
返回一个错误消息的字符串。  
  
## 语法  
  
```  
  
errorObj.message  
```  
  
## 参数  
 `errorObj`  
 必需。  `Error` 对象的实例。  
  
## 备注  
 `message` 属性返回一个包含与特定错误相关的错误消息的字符串。  
  
 `description` 和 `message` 属性提供了相同功能。  `description` 属性提供向后兼容性；`message` 属性符合 ECMA 标准。  
  
## 示例  
 下面的示例导致引发了 TypeError 异常，并显示了错误名称及其消息。  
  
```javascript  
try  
{  
    // Cause an error.  
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
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **适用于**：[Error 对象](../../javascript/reference/error-object-javascript.md)  
  
## 请参阅  
 [description 属性（错误）](../../javascript/reference/description-property-error-javascript.md)   
 [name 属性（错误）](../../javascript/reference/name-property-error-javascript.md)