---
title: "ignoreCase 属性（正则表达式）(JavaScript) | Microsoft Docs"
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
  - "ignoreCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "IgnoreCase 属性"
ms.assetid: 816f0df5-5a82-44a5-a4ab-dbc91fa76e61
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# ignoreCase 属性（正则表达式）(JavaScript)
返回布尔值，该值指示在正则表达式中使用的 ignoreCase 标志 \(**i**\) 的状态。  默认值为 **false**。  只读。  
  
## 语法  
  
```  
  
rgExp.ignoreCase  
```  
  
## 备注  
 必需的 `rgExp` 引用是 `RegExp` 对象的一个实例。  
  
 **ignoreCase** 属性在 ignoreCase 标志是为正则表达式设置时，返回 **true**，否则返回 **false**。  
  
 如果使用了 ignoreCase 标志，则该标志将指示被搜索字符串中执行模式匹配的一个搜索应该不区分大小写。  
  
## 示例  
 下面的示例阐释了 **ignoreCase** 属性的用法。  如果将“gi”传递到下面显示的函数中，“the”一词的所有实例（包括最初的“The”）都将替换为“a”一词。  这是因为，当设置了 ignoreCase 标志时，搜索将忽略大小写。  因此，在匹配时，“T”和“t”相同。  
  
 此函数返回布尔值，这些布尔值指示允许的正则表达式标志的状态 **g**、**i** 和 **m**。  此函数还返回进行了所有替换的字符串。  
  
```javascript  
function RegExpPropDemo(flag){  
    // The flag parameter is a string that contains  
    // g, i, or m. The flags can be combined.  
  
    // Check flags for validity.  
    if (flag.match(/[^gim]/))  
        {  
        return ("Flag specified is not valid");  
        }  
  
    // Create the string on which to perform the replacement.  
    var orig = "The batter hit the ball with the bat ";  
    orig += "and the fielder caught the ball with the glove.";  
  
    // Replace "the" with "a".  
    var re = new RegExp("the", flag);  
    var r = orig.replace(re, "a");          
  
    // Output the resulting string and the values of the flags.  
    var s = "";  
    s += "global: " + re.global.toString();  
    s += "<br />";  
    s += "ignoreCase: " + re.ignoreCase.toString();  
    s += "<br />";  
    s += "multiline: " + re.multiline.toString();  
    s += "<br />";  
    s += "Resulting String: " + r;  
    s += "<br />";  
    s += "<br />";  
    return (s);  
}  
  
document.write(RegExpPropDemo("gi"));  
document.write(RegExpPropDemo("g"));  
```  
  
## 示例  
 下面是结果输出。  
  
```javascript  
global: true  
ignoreCase: true  
multiline: false  
Resulting String: a batter hit a ball with a bat and a fielder caught a ball with a glove.  
  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**：[正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)  
  
## 请参阅  
 [global 属性（正则表达式）](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [multiline 属性（正则表达式）](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-cn/ab0766e1-7037-45ed-aa23-706f58358c0e)