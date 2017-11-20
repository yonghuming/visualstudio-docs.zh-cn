---
title: "JSON.stringify 函数 (JavaScript) |Microsoft 文档"
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
helpviewer_keywords: stringify method
ms.assetid: 0fafaf3b-c29b-46dc-b65b-ca223064a1d0
caps.latest.revision: "40"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3539bb003ed20a3ff7586e42466bf7c47165b83f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="jsonstringify-function-javascript"></a>JSON.stringify 函数 (JavaScript)
将 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 值转换为 JavaScript 对象表示法 (Json) 字符串。  
  
## <a name="syntax"></a>语法  
  
```  
  
JSON.stringify(  
value [, replacer] [, space])  
```  
  
## <a name="parameters"></a>参数  
 `value`  
 必需。 要转换的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 值（通常为对象或数组）。  
  
 `replacer`  
 可选。 用于转换结果的函数或数组。  
  
 如果 `replacer` 为函数，则 `JSON.stringify` 将调用该函数，并传入每个成员的键和值。 使用返回值而不是原始值。 如果此函数返回 `undefined`，则排除成员。 根对象的键是一个空字符串：""。  
  
 如果 `replacer` 是一个数组，则仅转换该数组中具有键值的成员。 成员的转换顺序与键在数组中的顺序一样。 当 `replacer` 参数也为数组时，将忽略 `value` 数组。  
  
 `space`  
 可选。 向返回值 JSON 文本添加缩进、空格和换行符以使其更易于读取。  
  
 如果省略 `space`，则将生成返回值文本，而没有任何额外空格。  
  
 如果 `space` 是一个数字，则返回值文本在每个级别缩进指定数目的空格。 如果 `space` 大于 10，则文本缩进 10 个空格。  
  
 如果 `space` 是一个非空字符串（例如“\t”），则返回值文本在每个级别中缩进字符串中的字符。  
  
 如果 `space` 是长度大于 10 个字符的字符串，则使用前 10 个字符。  
  
## <a name="return-value"></a>返回值  
 一个包含 JSON 文本的字符串。  
  
## <a name="exceptions"></a>异常  
  
|例外|条件|  
|---------------|---------------|  
|[无效的替换器参数](../../javascript/misc/invalid-replacer-argument.md)|`replacer` 参数不是函数或数组。|  
|[不支持在值参数中进行循环引用](../../javascript/misc/circular-reference-in-value-argument-not-supported.md)|`value` 参数包含循环引用。|  
  
## <a name="remarks"></a>备注  
 如果 `value` 具有 `toJSON` 方法，则 `JSON.stringify` 函数将使用该方法的返回值。 如果 `toJSON` 方法的返回值为 `undefined`，则不转换成员。 这使对象能够确定自己的 JSON 表示形式。  
  
 将不会转换不具有 JSON 表示形式的值，例如 `undefined`。 在对象中，将丢弃这些值。 在数组中，会将这些值替换为 null。  
  
 字符串值以引号开始和结束。 所有 Unicode 字符可括在引号中，但必须使用反斜杠进行转义的字符除外。 以下字符的前面必须是反斜杠：  
  
-   引号 (")  
  
-   反斜杠 (\\)  
  
-   退格键 (b)  
  
-   换页符 (f)  
  
-   换行符 (n)  
  
-   回车符 (r)  
  
-   水平制表符 (t)  
  
-   四个十六进制数字 (uhhhh)  
  
## <a name="order-of-execution"></a>执行顺序  
 在序列化过程中，如果 `toJSON` 参数对应有 `value` 方法，则 `JSON.stringify` 将首先调用 `toJSON` 方法。 如果该方法不存在，则使用原始值。 接下来，如果提供 `replacer` 参数，则该值（原始值或 `toJSON` 返回值）将替换为 `replacer` 参数的返回值。 最后，根据可选 `space` 参数向该值添加空格以生成最终的 JSON 文本。  
  
## <a name="example"></a>示例  
 此示例使用 `JSON.stringify` 将 `contact` 对象转换为 JSON 文本。 定义 `memberfilter` 数组以便只转换 `surname` 和 `phone` 成员。 省略 `firstname` 成员。  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Array();  
memberfilter[0] = "surname";  
memberfilter[1] = "phone";  
var jsonText = JSON.stringify(contact, memberfilter, "\t");  
document.write(jsonText);  
// Output:   
// { "surname": "Aaberg", "phone": [ "555-0100", "555-0120" ] }  
```  
  
## <a name="example"></a>示例  
 此示例将 `JSON.stringify` 与一个数组一起使用。 `replaceToUpper` 函数将数组中的每个字符串转换为大写形式。  
  
```JavaScript  
var continents = new Array();  
continents[0] = "Europe";  
continents[1] = "Asia";  
continents[2] = "Australia";  
continents[3] = "Antarctica";  
continents[4] = "North America";  
continents[5] = "South America";  
continents[6] = "Africa";  
  
var jsonText = JSON.stringify(continents, replaceToUpper);  
  
function replaceToUpper(key, value) {  
    return value.toString().toUpperCase();  
}  
  
//Output:  
// "EUROPE,ASIA,AUSTRALIA,ANTARCTICA,NORTH AMERICA,SOUTH AMERICA,AFRICA"  
  
```  
  
## <a name="example"></a>示例  
 此示例使用 `toJSON` 方法将字符串值转换为大写形式。  
  
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
document.write(jsonText);  
  
// Output:  
{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}  
  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [JSON.parse 函数](../../javascript/reference/json-parse-function-javascript.md)   
 [toJSON 方法 (Date)](../../javascript/reference/tojson-method-date-javascript.md)   
 [订阅源的阅读器示例应用程序 （Windows 应用商店）](http://code.msdn.microsoft.com/Feed-reader-sample-99d68cf8)