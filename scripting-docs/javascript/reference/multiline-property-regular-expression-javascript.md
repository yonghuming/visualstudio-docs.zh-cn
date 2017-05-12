---
title: "multiline 属性（正则表达式）(JavaScript) | Microsoft Docs"
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
  - "multiline"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "multiline 属性"
ms.assetid: ca7b276a-1fe2-4189-ac27-f089ab3e9974
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# multiline 属性（正则表达式）(JavaScript)
返回布尔值，该值指示在正则表达式中使用的 multiline 标志 \(**m**\) 的状态。  默认值为 **false**。  只读。  
  
## 语法  
  
```  
  
rgExp.multiline  
```  
  
## 备注  
 必需的 `rgExp` 参数是 `RegExp` 对象的实例  
  
 **multiline** 属性在 multiline 标志是为正则表达式设置时，返回 **true**，否则返回 **false**。  如果使用 **m** 标志创建正则表达式对象，那么 **multiline** 属性就是 **true**。  
  
 如果 **multiline** 为 **false**，那么“^”与字符串的开始位置相匹配，而“$”与字符串的结束位置相匹配。  如果 **multiline** 为 **true**，那么“^”与字符串开始位置以及“\\n”或“\\r”之后的位置相匹配，而“$”与字符串结束位置以及“\\n”或“\\r”之前的位置相匹配。  
  
## 示例  
 下面的示例阐释了 **multiline** 属性的行为。  如果将“m”传递到下面显示的函数中，“while”一词将替换为“and”一词。  这是因为设置了 multiline 标志，并且“while”一词出现在换行符后面一行的开头。  multiline 标志允许对多行字符串执行搜索。  
  
```javascript  
function RegExpMultilineDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The man hit the ball with the bat ";  
   ss += "\nwhile the fielder caught the ball with the glove.";  
  
   // Replace "while" with "and".  
   var re = new RegExp("^while", flag);  
   var r = ss.replace(re, "and");          
  
   // Output the multiline flag and the resulting string.  
   var s = "";  
   s += "Result for multiline = " + re.multiline.toString();  
   s += ": " + r;  
  
   return(s);  
  
}  
  
sa = RegExpMultilineDemo("m");  
sb = RegExpMultilineDemo("");  
document.write (sa + "<br />" + sb);  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**：[正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)  
  
## 请参阅  
 [global 属性（正则表达式）](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [ignoreCase 属性（正则表达式）](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-cn/ab0766e1-7037-45ed-aa23-706f58358c0e)