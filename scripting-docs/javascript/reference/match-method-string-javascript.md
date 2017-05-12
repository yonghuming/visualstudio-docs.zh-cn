---
title: "match 方法 (String) (JavaScript) | Microsoft Docs"
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
  - "match"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Match 方法"
ms.assetid: eda9ad27-4f9b-4cb1-8345-a0ae85979ca0
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# match 方法 (String) (JavaScript)
将字符串与正则表达式匹配，并返回一个包含该搜索结果的数组。  
  
## 语法  
  
```  
  
stringObj.match(rgExp)   
```  
  
## 参数  
 `stringObj`  
 必需。  执行搜索的 `String` 对象或字符串文本。  
  
 `rgExp`  
 必需。  包含正则表达式模式和适用标志的正则表达式对象。  这也可以是包含正则表达式模式和标志的变量名或字符串。  
  
## 备注  
 如果 `match` 方法没有找到匹配，将返回 `null`。  如果找到匹配，则 `match` 方法返回一个数组，并将更新全局 `RegExp` 对象的属性以反映匹配结果。  
  
 如果没有设置全局标志 \(`g`\)，数组元素 0 包含整个匹配，而元素 1 到 *n* 包含任何一个子匹配。  此行为与未设置全局标志时 [exec 方法（正则表达式）](../../javascript/reference/exec-method-regular-expression-javascript.md) 的行为相同。  如果设置了全局标志，则元素 0 到元素 *n* 包含所有出现的匹配。  
  
 如果未设置全局标志，则 `match` 方法返回的数组有两个特性：`input` 和 `index`。  `input` 属性包含整个被搜索的字符串。  `index` 属性包含了在整个被搜索字符串中匹配的子字符串的位置。  
  
 如果设置了标志 `i`，则搜索不区分大小写。  
  
## 示例  
 下面的示例演示 `match` 方法的用法。  
  
```javascript  
var src = "azcafAJAC";  
  
var re = /[a-c]/;  
  
var result = src.match(re);  
  
// The entire match is in array element 0.  
document.write(result[0] + "<br/>");  
  
// Now try the same match with the global flag.  
var reg = /[a-c]/g;  
result = src.match(reg);  
  
// The matches are in elements 0 through n.  
for (var index = 0; index < result.length; index++)  
{  
    document.write ("submatch " + index + ": " +  result[index]);  
    document.write("<br />");  
}  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **应用于**：[String 对象](../../javascript/reference/string-object-javascript.md)  
  
## 请参阅  
 [exec 方法（正则表达式）](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [RegExp 对象](../../javascript/reference/regexp-object-javascript.md)   
 [正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)   
 [replace 方法 \(String\)](../../javascript/reference/replace-method-string-javascript.md)   
 [search 方法 \(String\)](../../javascript/reference/search-method-string-javascript.md)   
 [test 方法（正则表达式）](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/zh-cn/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Alternation and Subexpressions \(JavaScript\)](http://msdn.microsoft.com/zh-cn/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Backreferences \(JavaScript\)](http://msdn.microsoft.com/zh-cn/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)