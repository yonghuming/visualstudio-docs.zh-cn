---
title: "lastIndex 属性 (RegExp) (JavaScript) | Microsoft Docs"
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
  - "lastIndex"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lastIndex 属性"
ms.assetid: c8ae2a13-6dff-4cbe-b662-aca3d66c2a7f
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# lastIndex 属性 (RegExp) (JavaScript)
返回字符的位置，该位置是被搜索字符串中下一次匹配的开始位置。  
  
## 语法  
  
```  
  
RegExp.lastIndex  
```  
  
## 备注  
 与此属性关联的对象始终为全局 `RegExp` 对象。  
  
 `lastIndex` 属性是从零开始的，也就是说，第一个字符的索引是零。  初始值为 –1。  无论何时产生一个成功匹配，其值都被修改。  
  
 `lastIndex` 属性是由 `RegExp` 对象的 `exec` 和 **test** 方法以及 `String` 对象的 `match`、**replace** 和 **split** 方法修改的。  
  
 下面的规则适用于 `lastIndex` 的值：  
  
-   如果没有匹配，则 `lastIndex` 被设置为 \-1。  
  
-   如果 `lastIndex` 大于字符串的长度，则 **test** 和 `exec` 失败，并且 `lastIndex` 被设置为 \-1。  
  
-   如果 `lastIndex` 等于字符串的长度，且模式与空字符串匹配，则正则表达式匹配。  否则，匹配失败并且 `lastIndex` 被重新设置为 \-1。  
  
-   否则，`lastIndex` 被设置为紧接最近的匹配的下一个位置。  
  
## 示例  
 下面的示例演示如何使用 `lastIndex` 属性。  该函数重复一个字符串搜索，并打印出字符串中每一个词的 **index** 和 `lastIndex` 值。  
  
```javascript  
function RegExpTest()  
{  
   var ver = Number(ScriptEngineMajorVersion() + "." + ScriptEngineMinorVersion())  
   if (ver < 5.5)  
   {  
      document.write("You need a newer version of JavaScript for this to work");  
      return;  
   }  
  
   var src = "The quick brown fox jumps over the lazy dog.";  
  
   // Create regular expression pattern with a global flag.  
   var re = /\w+/g;  
  
   // Get the next word, starting at the position of lastindex.  
   var arr;  
   while ((arr = re.exec(src)) != null)  
      {  
      // New line:  
      document.write ("<br />");    
      document.write (arr.index + "-" + re.lastIndex + " ");  
      document.write (arr);  
      }  
}  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **应用于**：[RegExp 对象](../../javascript/reference/regexp-object-javascript.md)  
  
## 请参阅  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-cn/ab0766e1-7037-45ed-aa23-706f58358c0e)