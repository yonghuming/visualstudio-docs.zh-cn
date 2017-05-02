---
title: "toJSON 方法 (Date) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toJSON 方法"
ms.assetid: f91df030-e9c9-425e-8e6d-b46bdda66cb6
caps.latest.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 27
---
# toJSON 方法 (Date) (JavaScript)
由 [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md) 方法用于允许转换某个对象的数据以进行 JavaScript Object Notation \(JSON\) 序列化。  
  
## 语法  
  
```  
  
objectname.toJSON()  
```  
  
## 参数  
 `objectname`  
 必需。  需要进行 JSON 序列化的对象。  
  
## 备注  
 `toJSON` 方法由 `JSON.stringify` 函数使用。  `JSON.stringify` 将 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 值序列化为 JSON 文本。  如果向 `JSON.stringify` 提供了 `toJSON` 方法，则在调用 `JSON.stringify` 时将调用 `toJSON` 方法。  
  
 `toJSON` 方法是 [Date](../../javascript/reference/date-object-javascript.md) [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 对象的内置成员。  它返回 UTC 时区的 ISO 格式日期字符串（由后缀 Z 表示）。  
  
 可重写 `Date` 类型的 `toJSON` 方法，也可为其他对象类型定义 `toJSON` 方法，以实现在 JSON 序列化之前对特定对象类型进行数据转换。  
  
## 示例  
 以下示例使用 `toJSON` 方法将大写的字符串成员值序列化。  在调用 `JSON.stringify` 时调用 `toJSON` 方法。  
  
```javascript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
  
/* The value of jsonText is:  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## 示例  
 以下示例演示如何使用作为 [Date](../../javascript/reference/date-object-javascript.md) 对象的内置成员的 `toJSON` 方法。  
  
```javascript  
var dt = new Date('8/24/2009');  
dt.setUTCHours(7, 30, 0);  
var jsonText = JSON.stringify(dt);  
  
/* The value of jsonText is:  
'"2009-08-24T07:30:00Z"'  
*/  
```  
  
## 要求  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)] **适用于：** [Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [JSON 对象](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse 函数](../../javascript/reference/json-parse-function-javascript.md)   
 [JSON.stringify 函数](../../javascript/reference/json-stringify-function-javascript.md)   
 [JavaScript 方法](../../javascript/reference/javascript-methods.md)