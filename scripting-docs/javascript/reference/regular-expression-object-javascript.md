---
title: "正则表达式对象 (JavaScript) | Microsoft Docs"
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
  - "RegularExpression_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "RegExp 对象, 概述"
  - "正则表达式对象"
  - "正则表达式, RegExp 对象"
ms.assetid: 346aa83e-a045-47ea-acae-b42c7b121534
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# 正则表达式对象 (JavaScript)
一个对象，该对象包含正则表达式模式以及标识如何应用该模式的标志。  
  
## 语法  
  
```  
re = /pattern/[flags]  
```  
  
## 语法  
  
```  
re = new RegExp("pattern"[,"flags"])   
```  
  
## 参数  
 *re*  
 必需。  正则表达式模式分配到的变量名称。  
  
 *pattern*  
 必需。  要使用的正则表达式模式。  如果使用语法 1，则用“\/”字符分隔模式。  如果使用语法 2，则将模式用引号引起来。  
  
 `flags`  
 可选。  如果使用语法 2，则将标志用引号引起来。  可以组合的可用标志包括：  
  
-   g（全局搜索出现的所有*模式*）  
  
-   i（忽略大小写）  
  
-   m（多行搜索）  
  
-   u \(unicode\)，启用 EcmaScript 6 [Unicode 功能](../../javascript/advanced/special-characters-javascript.md)。  仅在 [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] 中受支持。  
  
-   y（粘滞匹配），在正则表达式的 `lastIndex` 属性处搜索匹配项（而不是在后面的索引处搜索）。  在 [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)] 中受支持。  
  
## 备注  
 不应将**正则表达式**对象与全局 `RegExp` 对象相混淆。  即使它们看起来相同，但它们彼此独立，截然不同。  **正则表达式**对象的属性只包含有关一个特定**正则表达式**实例的信息，而全局 `RegExp` 对象的属性则包含有关所发生的每一个匹配的持续更新的信息。  
  
 **正则表达式**对象存储在搜索字符组合的字符串时使用的模式。  在创建**正则表达式**对象后，会将该对象传递到字符串方法，或将字符串传递到某个正则表达式方法。  关于最近执行的搜索信息存储在全局 `RegExp` 对象中。  
  
 当预先知晓搜索字符串时，使用语法 1.  当搜索字符串频繁更改或未知时（例如，来自用户输入的字符串），使用语法 2.  
  
 *pattern* 参数将在使用之前编译为内部格式。  对于语法 1，在加载脚本时编译 *pattern*。  对于语法 2，在使用之前编译 *pattern*，或者在调用 **compile** 方法时进行编译。  
  
## 示例  
 下面的示例通过创建包含带其关联标志的正则表达式模式的对象 \(re\) 来阐释**正则表达式**对象的用法。  在此示例中，生成的**正则表达式**对象随后将由 `match` 方法使用：  
  
```javascript  
var s = "through the pages of the book";  
  
// Create regular expression pattern.  
var re = new RegExp("the", "i");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return first occurrence of "the".  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
//   
```  
  
## 示例  
 下面的示例更新了正则表达式模式以便搜索多个实例。  
  
```javascript  
// Create regular expression pattern using the i and g flags.  
var re = new RegExp("the", "ig");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return the two occurrences of "the".  
if(console && console.log) {  
    console.log(r.length);  
    console.log(r);  
}  
  
// Output:  
// 2  
// [object Array] ["the", "the"]  
```  
  
## 示例  
 使用 \/y 标志时，如果匹配成功，则该标志会将 `lastindex` 更新为最后一个匹配项后的下一个字符的索引。  如果匹配失败，则该标志会将 `lastindex` 重置为 0。  
  
 下面的示例使用 \/y 标志和`lastIndex` 属性在特定索引处搜索匹配项。  
  
```javascript  
// Create regular expression pattern using the i and y flags.  
var re = new RegExp("the", "iy");  
  
// Set the lastIndex property and attempt a match  
// at the specified index.  
re.lastIndex = 20;  
var r = s.match(re);     
  
// No matches returned.  
if(console && console.log) {  
    console.log(r);  
}  
// Reset the lastIndex property and attempt a match.  
re.lastIndex = 21;  
var r = s.match(re);  
  
// Return occurrence of "the" starting at index 21.  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
// null  
// [object Array] ["the"]  
```  
  
<a name="js56jsobjregexpressionprop"></a>   
## 属性  
 [global 属性](../../javascript/reference/global-property-regular-expression-javascript.md) &#124; [ignoreCase 属性](../../javascript/reference/ignorecase-property-regular-expression-javascript.md) &#124; [multiline 属性](../../javascript/reference/multiline-property-regular-expression-javascript.md) &#124; [source 属性](../../javascript/reference/source-property-regular-expression-javascript.md)  
  
<a name="js56jsobjregexpressionmeth"></a>   
## 方法  
 [compile 方法](../../javascript/reference/compile-method-regular-expression-javascript.md) &#124; [exec 方法](../../javascript/reference/exec-method-regular-expression-javascript.md) &#124; [test 方法](../../javascript/reference/test-method-regular-expression-javascript.md)  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 u 标志在 [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] 中受支持。  
  
 y 标志在 [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)] 中受支持。  
  
## 请参阅  
 [RegExp 对象](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-cn/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [String 对象](../../javascript/reference/string-object-javascript.md)