---
title: "RegExp 对象 (JavaScript) | Microsoft Docs"
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
  - "RegExp"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "RegExp 对象"
  - "RegExp 对象, 概述"
ms.assetid: 7f6b1073-8cbb-49ed-94b6-56833ba663c5
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# RegExp 对象 (JavaScript)
内部全局对象，它存储有关正则表达式模式匹配结果的信息。  
  
## 语法  
  
```  
  
RegExp.property   
```  
  
## 备注  
 必需的 *property* 参数可以是任何一个 `RegExp` 对象属性。  
  
 `RegExp` 对象不能直接创建，但它始终可用。  在完成成功的正则表达式搜索之前，`RegExp` 对象的各种属性具有如下初始值：  
  
|属性|简写|初始值|  
|--------|--------|---------|  
|index||\-1|  
|input|$\_|空字符串。|  
|lastIndex||\-1|  
|lastMatch|$&|空字符串。|  
|lastParen|$\+|空字符串。|  
|leftContext|$\`|空字符串。|  
|rightContext|$'|空字符串。|  
|$1 \- $9|$1 \- $9|空字符串。|  
  
 在成功完成正则表达式搜索之前，其属性将 undefined 作为其值。  
  
 不应将全局 `RegExp` 对象与 **Regular Expression** 对象混淆。  即使它们看起来相同，但它们是完全不同且相互分离的。  全局 `RegExp` 对象的属性包含有关所发生的每一匹配的不断更新的信息，而 **Regular Expression** 对象的属性只包含有关与 **Regular Expression** 实例发生的匹配的信息。  
  
## 示例  
 下面的示例执行正则表达式搜索。  它显示了来自全局 `RegExp` 对象和由 `exec` 方法返回的数组的匹配项和子匹配项。  
  
```javascript  
var newLine = "<br />";  
  
var re = /(\w+)@(\w+)\.(\w+)/g  
var src = "Please send mail to george@contoso.com and someone@example.com. Thanks!"  
  
var result;  
var s = "";  
  
// Get the first match.  
result = re.exec(src);  
  
while (result != null) {  
    // Show the entire match.  
    s += newLine;  
  
    // Show the match and submatches from the RegExp global object.  
    s += "RegExp.lastMatch: " + RegExp.lastMatch + newLine;  
    s += "RegExp.$1: " + RegExp.$1 + newLine;  
    s += "RegExp.$2: " + RegExp.$2 + newLine;  
    s += "RegExp.$3: " + RegExp.$3 + newLine;  
  
    // Show the match and submatches from the array that is returned  
    // by the exec method.  
    for (var index = 0; index < result.length; index++) {  
        s +=  index + ": ";  
        s += result[index];  
        s += newLine;  
    }  
  
    // Get the next match.  
    result = re.exec(src);  
}  
document.write(s);  
  
// Output:  
//  RegExp.lastMatch: george@contoso.com  
//  RegExp.$1: george  
//  RegExp.$2: contoso  
//  RegExp.$3: com  
//  0: george@contoso.com  
//  1: george  
//  2: contoso  
//  3: com  
  
//  RegExp.lastMatch: someone@example.com  
//  RegExp.$1: someone  
//  RegExp.$2: example  
//  RegExp.$3: com  
//  0: someone@example.com  
//  1: someone  
//  2: example  
//  3: com  
  
```  
  
<a name="js56jsobjregexpprop"></a>   
## 属性  
 [$1...$9 属性](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md) &#124; [index 属性](../../javascript/reference/index-property-regexp-javascript.md) &#124; [input 属性](../../javascript/reference/input-property-dollar-regexp-javascript.md) &#124; [lastIndex 属性](../../javascript/reference/lastindex-property-regexp-javascript.md) &#124; [lastMatch 属性](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md) &#124; [lastParen 属性](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md) &#124; [leftContext 属性](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md) &#124; [rightContext 属性](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)  
  
## 方法  
 `RegExp` 对象没有方法。  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 请参阅  
 [正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-cn/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [String 对象](../../javascript/reference/string-object-javascript.md)