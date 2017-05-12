---
title: "JSON.parse 函数 (JavaScript) | Microsoft Docs"
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
  - "JSON.parse"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JSON.parse 方法"
  - "parse JSON 方法"
ms.assetid: 20f00d31-5ab5-4c3c-ab49-2534fc39a9b4
caps.latest.revision: 41
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 41
---
# JSON.parse 函数 (JavaScript)
将 JavaScript 对象表示法 \(JSON\) 字符串转换为对象。  
  
## 语法  
  
```  
JSON.parse(text [, reviver])  
```  
  
## 参数  
 `text`  
 必需。 一个有效的 JSON 字符串。  
  
 `reviver`  
 可选。 一个转换结果的函数。 将为对象的每个成员调用此函数。 如果成员包含嵌套对象，则先于父对象转换嵌套对象。 对于每个成员，会发生以下情况：  
  
-   如果 `reviver` 返回一个有效值，则成员值将替换为转换后的值。  
  
-   如果 `reviver` 返回它接收的相同值，则不修改成员值。  
  
-   如果 `reviver` 返回 `null` 或 `undefined`，则删除了该成员。  
  
## 返回值  
 一个对象或数组。  
  
## 异常  
 如果此函数引发 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 分析器错误（如“SCRIPT1014：无效字符”），则输入文本将不遵循 JSON 语法。 若要更正此错误，请执行下列操作之一：  
  
-   修改 `text` 参数以遵循 JSON 语法。 有关更多信息，请参见 JSON 对象的 [BNF 语法表示法](http://go.microsoft.com/fwlink/?LinkId=125203)。  
  
     例如，如果响应的格式为 JSONP 而非纯 JSON，请在响应对象上尝试此代码：  
  
    ```javascript  
    var fixedResponse = response.responseText.replace(/\\'/g, "'");  
    var jsonObj = JSON.parse(fixedResponse);  
    ```  
  
-   确保通过 JSON 兼容的实现（如 `text`）对 `JSON.stringify` 参数进行序列化。  
  
-   在 JSON 验证程序（如 [JSLint](http://www.jslint.com/)）中运行 `text` 参数以帮助找到语法错误。  
  
## 示例  
 以下示例使用 `JSON.parse` 将 JSON 字符串转换成对象。  
  
```javascript  
var jsontext = '{"firstname":"Jesper","surname":"Aaberg","phone":["555-0100","555-0120"]}';  
var contact = JSON.parse(jsontext);  
document.write(contact.surname + ", " + contact.firstname);  
document.write(contact.phone[1]);  
// Output:  
// Aaberg, Jesper  
// 555-0100  
```  
  
## 示例  
 以下示例演示了如何使用 `JSON.stringify` 将数组转换成 JSON 字符串，然后使用 `JSON.parse` 将该字符串重新转换成数组。  
  
```javascript  
var arr = ["a", "b", "c"];  
var str = JSON.stringify(arr);  
document.write(str);  
document.write ("<br/>");  
  
var newArr = JSON.parse(str);  
  
while (newArr.length > 0) {  
    document.write(newArr.pop() + "<br/>");  
}  
  
// Output:  
// ["a","b","c"]  
// c  
// b  
// a  
```  
  
## 示例  
 `reviver` 函数通常用于将国际标准化组织 \(ISO\) 日期字符串的 JSON 表示形式转换为协调世界时 \(UTC\) 格式`日期`对象。 此示例使用 `JSON.parse` 来反序列化 ISO 格式的日期字符串。`dateReviver` 函数为格式为 ISO 日期字符串的成员返回 `Date` 对象。  
  
```javascript  
var jsontext = '{ "hiredate": "2008-01-01T12:00:00Z", "birthdate": "2008-12-25T12:00:00Z" }';  
var dates = JSON.parse(jsontext, dateReviver);  
document.write(dates.birthdate.toUTCString());  
  
function dateReviver(key, value) {  
    var a;  
    if (typeof value === 'string') {  
        a = /^(\d{4})-(\d{2})-(\d{2})T(\d{2}):(\d{2}):(\d{2}(?:\.\d*)?)Z$/.exec(value);  
        if (a) {  
            return new Date(Date.UTC(+a[1], +a[2] - 1, +a[3], +a[4],  
                            +a[5], +a[6]));  
        }  
    }  
    return value;  
};  
  
// Output:  
// Thu, 25 Dec 2008 12:00:00 UTC  
  
```  
  
## 要求  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## 请参阅  
 [JSON.stringify 函数](../../javascript/reference/json-stringify-function-javascript.md)   
 [toJSON 方法 \(Date\)](../../javascript/reference/tojson-method-date-javascript.md)   
 [中心模板示例应用（Windows 应用商店）](http://code.msdn.microsoft.com/Hub-template-sample-with-4b70002d)