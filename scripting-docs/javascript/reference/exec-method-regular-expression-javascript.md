---
title: "exec 方法（正则表达式）(JavaScript) | Microsoft Docs"
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
  - "exec"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Exec 方法"
  - "匹配字符串"
ms.assetid: 83092452-60cc-4218-b4ae-af9e3cb96c34
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# exec 方法（正则表达式）(JavaScript)
使用正则表达式模式对字符串执行搜索，并返回一个包含该搜索结果的数组。  
  
## 语法  
  
```  
  
rgExp.exec(str)   
```  
  
## 参数  
 `rgExp`  
 必需。  包含正则表达式模式和适用标志的 **Regular Expression** 对象的实例。  
  
 `str`  
 必需。  对其执行搜索的 `String` 对象或字符串文本。  
  
## 备注  
 如果 `exec` 方法没有找到匹配，将返回 `null`。  如果找到匹配项，则 `exec` 方法返回一个数组，并将更新全局 `RegExp` 对象的属性以反映匹配结果。  数组元素 0 包含了完整的匹配项，而元素 1 到 *n* 包含的是匹配项中出现的任意一个子匹配项。  这相当于没有设置全局标志 \(**g**\) 的 `match` 方法的行为。  
  
 如果为正则表达式设置了全局标志，则 `exec` 从 `lastIndex` 值指示的位置开始搜索字符串。  如果没有设置全局标志，则 `exec` 忽略 `lastIndex` 的值，从字符串的起始位置开始搜索。  
  
 `exec` 方法返回的数组有三个属性：**input**、**index** 和 **lastIndex**。**input** 属性包含整个被搜索的字符串。  **index** 属性包含了在整个被搜索字符串中匹配的子字符串的位置。  `lastIndex` 属性中包含了匹配中最后一个字符的下一个位置。  
  
## 示例  
 下面的示例阐释了 `exec` 方法的用法：  
  
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
      document.write (arr.index + "-" + arr.lastIndex + " ");  
      document.write (arr[0]);  
      }  
}  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)  
  
## 请参阅  
 [match 方法 \(String\)](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp 对象](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-cn/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [search 方法 \(String\)](../../javascript/reference/search-method-string-javascript.md)   
 [test 方法（正则表达式）](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/zh-cn/3b62e27c-4f07-4726-a95b-6e841807bfaf)