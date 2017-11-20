---
title: "toJSON 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toJSON method
ms.assetid: f91df030-e9c9-425e-8e6d-b46bdda66cb6
caps.latest.revision: "27"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a131c7b248ca0486ab0b3b02d40e4351136c37c9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="tojson-method-date-javascript"></a>toJSON 方法 (Date) (JavaScript)
使用[JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)方法，以使 JavaScript 对象表示法 (JSON) 序列化的对象的数据的转换。  
  
## <a name="syntax"></a>语法  
  
```  
  
objectname.toJSON()  
```  
  
## <a name="parameters"></a>参数  
 `objectname`  
 必需。 Json 序列化还需要一个对象。  
  
## <a name="remarks"></a>备注  
 `toJSON`方法由`JSON.stringify`函数。 `JSON.stringify`序列化[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]值转换为 JSON 文本。 如果`toJSON`方法提供给`JSON.stringify`、`toJSON`方法调用时`JSON.stringify`调用。  
  
 `toJSON`方法是内置的成员[日期](../../javascript/reference/date-object-javascript.md)[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]对象。 它将返回 UTC 时区 （由后缀 Z 表示） 为 ISO 格式的日期字符串。  
  
 您可以重写`toJSON`方法`Date`类型，或者定义`toJSON`的其他对象类型实现的数据的 JSON 序列化之前的特定对象类型的转换的方法。  
  
## <a name="example"></a>示例  
 下面的示例使用`toJSON`要序列化以大写形式的字符串成员值的方法。 `toJSON`方法调用时`JSON.stringify`调用。  
  
```JavaScript  
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
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`toJSON`方法是内置成员的[日期](../../javascript/reference/date-object-javascript.md)对象。  
  
```JavaScript  
var dt = new Date('8/24/2009');  
dt.setUTCHours(7, 30, 0);  
var jsonText = JSON.stringify(dt);  
  
/* The value of jsonText is:  
'"2009-08-24T07:30:00Z"'  
*/  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]**适用于：** [日期对象](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [JSON 对象](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse 函数](../../javascript/reference/json-parse-function-javascript.md)   
 [JSON.stringify 函数](../../javascript/reference/json-stringify-function-javascript.md)   
 [JavaScript 方法](../../javascript/reference/javascript-methods.md)