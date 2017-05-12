---
title: "replace 方法 (String) (JavaScript) | Microsoft Docs"
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
  - "replace"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Replace 方法"
  - "替换字符串"
ms.assetid: 5f0e4765-df4d-4887-bd09-efe5e58251bf
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# replace 方法 (String) (JavaScript)
使用正则表达式或搜索字符串替换字符串中的文本。  
  
## 语法  
  
```  
  
stringObj. replace(rgExp, replaceText)  
```  
  
## 参数  
 `stringObj`  
 必需。  要执行替换的 `String` 对象或字符串文本。  **replace** 方法不会修改此字符串。  相反，此方法的返回值是替换所生成的字符串。  
  
 `rgExp`  
 必需。  包含正则表达式模式和适用标志的**正则表达式**对象的实例。  也可以是表示正则表达式的 `String` 对象或字符串文本。  如果 `rgExp` 不是**正则表达式**对象的实例，则将它转换为字符串，并对结果执行精确搜索；不会尝试将字符串转换为正则表达式。  
  
 `replaceText`  
 必需。  一个 `String` 对象或字符串文本，其中包含用于替换 `stringObj` 中 `rgExp` 的每个成功匹配项的文本。  在 [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] 或更高版本中，`replaceText` 参数也可以是返回替换文本的函数。  
  
## 返回值  
 在完成指定的替换之后，**replace** 方法的结果是 `stringObj` 的副本。  
  
## 备注  
 以下任一匹配变量均可用于标识最新的匹配项及其所在的字符串。  可以在必须动态确定替换字符串的文本替换中使用匹配变量。  
  
|字符|含义|  
|--------|--------|  
|**$$**|`$`（[!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] 或更高版本）|  
|**$&**|指定 `stringObj` 中匹配整个模式的部分。  （[!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] 或更高版本）|  
|`$``|指定 `stringObj` 中位于 **$&** 所描述的匹配项前面的部分。  （[!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] 或更高版本）|  
|`$'`|指定 `stringObj` 中位于 **$&** 所描述的匹配项后面的部分。  （[!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] 或更高版本）|  
|`$`  ***n***|第 *n* 个捕获到的子匹配，其中 *n* 为从 1 到 9 的十进制一位数。  （[!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] 或更高版本）|  
|`$`  ***nn***|第 *nn* 个捕获到的子匹配，其中 *nn* 为从 01 到 99 的十进制二位数。  （[!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] 或更高版本）|  
  
 如果 `replaceText` 是一个函数，则对于每个匹配的子字符串，调用此函数时使用下面的 *m* \+ 3 个参数，其中 *m* 是在 `rgExp` 中用于捕获的左括弧的个数。  第一个参数是匹配的子字符串。  接下来的 *m* 参数是搜索产生的所有捕获。  参数 *m* \+ 2 是发生匹配的 `stringObj` 中的偏移量，而参数 *m* \+ 3 是 `stringObj`。  结果是将每一个匹配的子字符串替换为函数调用的相应返回值后的字符串值。  
  
 **Replace** 方法将更新全局 `RegExp` 对象的属性。  
  
## 示例  
 下面的示例阐释了如何使用 **replace** 方法将“the”的所有实例替换为“a”。  
  
```javascript  
var s = "the batter hit the ball with the bat";  
  
// Replace "the" with "a".  
var re = /the/g;  
var result = s.replace(re, "a");  
document.write(result);  
// Output: a batter hit a ball with a bat  
```  
  
 另外，**replace** 方法也可以替换模式中的子表达式。  下面的示例将字符串中的每对单词进行了交换：  
  
```javascript  
  
var s = "The quick brown fox jumped over the lazy dog.";  
var re = /(\S+)(\s+)(\S+)/g;  
// Exchange each pair of words.  
var result = s.replace(re, "$3$2$1");  
document.write(result);  
  
// Output:  quick The fox brown over jumps lazy the dog.  
```  
  
 下面的示例（在 [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] 及更高版本中运行）演示如何使用返回替换文本的函数。  它将后跟“F”的任何数字实例替换为摄氏度转换值。  
  
```javascript  
function f2c(s1) {  
    // Initialize pattern.  
    var test = /(\d+(\.\d*)?)F\b/g;  
  
    // Use a function for the replacement.  
    var s2 = s1.replace(test,  
      function($0,$1,$2)  
           {   
           return((($1-32) * 5/9) + "C");  
           }  
        )  
    return s2;  
}  
document.write(f2c("Water freezes at 32F and boils at 212F."));  
  
// Output: Water freezes at 0C and boils at 100C.  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**：[String 对象](../../javascript/reference/string-object-javascript.md)  
  
## 请参阅  
 [exec 方法（正则表达式）](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [match 方法 \(String\)](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp 对象](../../javascript/reference/regexp-object-javascript.md)   
 [search 方法 \(String\)](../../javascript/reference/search-method-string-javascript.md)   
 [test 方法（正则表达式）](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/zh-cn/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Alternation and Subexpressions \(JavaScript\)](http://msdn.microsoft.com/zh-cn/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Backreferences \(JavaScript\)](http://msdn.microsoft.com/zh-cn/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)   
 [HTML5 拖放示例应用](http://code.msdn.microsoft.com/Drag-and-drop-e2701a72)