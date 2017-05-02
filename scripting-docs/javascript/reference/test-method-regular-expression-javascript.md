---
title: "test 方法（正则表达式）(JavaScript) | Microsoft Docs"
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
  - "test"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "测试方法"
ms.assetid: 4f4b6e39-cb1a-4be9-a66f-7b846075580d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# test 方法（正则表达式）(JavaScript)
返回一个布尔值，该值指示在搜索字符串中是否存在一种模式。  
  
## 语法  
  
```  
  
rgExp.test(str)   
```  
  
## 参数  
 `rgExp`  
 必需。  包含正则表达式模式和适用标志的 **Regular Expression** 对象的实例。  
  
 `str`  
 必需。  将对其执行搜索的字符串。  
  
## 备注  
 **test** 方法检查字符串中是否存在某种模式，如果存在，则返回 **true**，否则返回 **false**。  
  
 **test** 方法不修改全局 `RegExp` 对象的属性。  
  
## 示例  
 下面的示例阐释了 **test** 方法的用法。  若要使用此示例，请给函数传递一个正则表达式模式和一个字符串。  该函数会在字符串中检测正则表达式模式的匹配项并返回一个指示此搜索结果的字符串：  
  
```javascript  
function TestDemo(re, teststring)  
{  
   // Test string for existence of regular expression.  
   var found = re.test(teststring)  
  
   // Format the output.  
   var s = "";  
   s += "'" + teststring + "'"  
  
   if (found)  
      s += " contains ";  
   else  
      s += " does not contain ";  
  
   s += "'" + re.source + "'"  
   return(s);  
}  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)  
  
## 请参阅  
 [RegExp 对象](../../javascript/reference/regexp-object-javascript.md)   
 [正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-cn/ab0766e1-7037-45ed-aa23-706f58358c0e)