---
title: "模板字符串 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f2e525a5-b0fc-49c3-95a0-641788e5c12a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 模板字符串 (JavaScript)
在 [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] 中，可以使用模板字符串来构造具有嵌入式表达式的字符串文本。  模板字符串还为多行字符串提供内置支持。  
  
 若要构造模板字符串，请使用重读符号（也称为反引号）\('\) 替代单引号或双引号括起字符串。  下面的代码示例演示一个简单的模板字符串。  
  
```  
`Template strings can include 'single quotes' and "double quotes" inline.`  
  
```  
  
 模板字符串可以在无需使用换行符 \(\\n\) 的情况下包含换行。  
  
```  
`Template strings can include line breaks and don't need the linefeed character.`  
```  
  
 $ 字符用于指定模板字符串内的占位符。  语法是 ${*表达式*}，其中*表达式*是任意 JavaScript 表达式（如变量或函数），如以下示例中所示。  
  
```  
var name = "Bob";  
var str = `Hello ${name}, how are you this fine ${partOfDay()}?`  
console.log(str);  
  
function partOfDay () {  
    var hour = new Date().getHours();  
  
    if (hours <= 12) {  
        return “morning”;  
    } else if (hours <= 5) {  
        return “afternoon”;  
    } else {  
        return “evening”;  
    }  
}  
  
// Output:  
// Hello Bob, how are you this fine afternoon?  
```  
  
 带标记的模板函数，它可以通过使用由模板字符串中参数调用的函数来修改此模板字符串的值。  第一个参数是字符串文本的数组，由内含的模板字符串表达式分隔；第二个参数是包含模板字符串表达式的值的数组（[Rest 参数](../../javascript/functions-javascript.md)）。  
  
 在以下示例中，带标记的模板函数 buildURL 用于构造 URL。  此语法要使用后面紧跟模板字符串的函数名。  
  
```  
function buildURL(strArray, ...valArray) {  
    var newUrl = strArray[0] + "ja-ja" + "/" + valArray[1] +  
    "/" + valArray[2];  
  
    return newUrl;  
}  
  
var lang = "en-us";  
var a = "library";  
var b = "dn771551.aspx";  
  
// Call the tagged template function.  
var url = buildURL`http://msdn.microsoft.com/${lang}/${a}/${b}`;  
  
console.log(url);  
  
// Output:  
// http://msdn.microsoft.com/ja-ja/library/dn771551.aspx  
```  
  
 如果需要访问传入的原始字符串值，则传递给带标记的模板函数的第一个参数支持可返回传入字符串的原始字符串形式的 `raw` 属性。  
  
```  
function buildURL(strArray, ...valArray) {  
    console.log(strArray.raw);  
}  
  
var lang = "en-us";  
var a = "library";  
var b = "dn771551.aspx";  
  
// Call the tagged template function.  
var url = buildURL`http://msdn.microsoft.com/${lang}/${a}/${b}`;  
  
// Ouput:  
// http://msdn.microsoft.com/  
// /  
// en-us  
// library  
```  
  
> [!NOTE]
>  还可以使用 [String.raw](../../javascript/reference/string-raw-function-javascript.md) 函数返回模板字符串的原始字符串形式。  
  
## 请参阅  
 [JavaScript 语言参考](../../javascript/javascript-language-reference.md)   
 [高级 JavaScript](../../javascript/advanced/advanced-javascript.md)