---
title: "global 属性（正则表达式）(JavaScript) | Microsoft Docs"
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
  - "Global"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "global 属性"
ms.assetid: 76a0f115-0d89-4aca-86d5-932895c6d649
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# global 属性（正则表达式）(JavaScript)
返回布尔值，该值指示使用正则表达式的 global 标志 \(**g**\) 的状态。  默认值为 **false**。  只读。  
  
## 语法  
  
```  
  
rgExp.global  
```  
  
## 备注  
 必需的 `rgExp` 引用是 **Regular Expression** 对象的一个实例。  
  
 `global` 属性在为正则表达式设置全局标志时返回 **true**，否则返回 **false**。  
  
 当使用全局标志时，它将指示一个搜索操作应找到被搜索字符串中的所有模式，而不仅仅是第一个。  这也称为全局匹配。  
  
## 示例  
 下面的示例阐释了 `global` 属性的用法。  如果将 **g** 传递到下面显示的函数中，“the”一词的所有实例都将替换为“a”一词。  请注意，不会替换字符串开头的“The”，因为 **i**（忽略大小写）标志未传递到函数。  
  
 此函数显示与允许的正则表达式标志关联的属性条件，它们是 **g**、**i** 和 **m**。  此函数还显示进行了所有替换的字符串。  
  
```javascript  
function RegExpPropDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The batter hit the ball with the bat ";  
   ss += "and the fielder caught the ball with the glove.";  
  
   //Replace "the" with "a".  
   var re = new RegExp("the", flag);  
   var r = ss.replace(re, "a");          
  
   // Output the resulting string and the flags.  
   var s = "";  
   s += "global: " + re.global.toString();  
   s += "<br />";  
   s += "ignoreCase: " + re.ignoreCase.toString();  
   s += "<br />";  
   s += "multiline: " + re.multiline.toString();  
   s += "<br />";  
   s += "Resulting String: " + r;  
  
   return (s);  
}  
  
document.write(RegExpPropDemo("g"));  
```  
  
## 示例  
 下面是结果输出。  
  
```javascript  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**：[正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)  
  
## 请参阅  
 [ignoreCase 属性（正则表达式）](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [multiline 属性（正则表达式）](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-cn/ab0766e1-7037-45ed-aa23-706f58358c0e)