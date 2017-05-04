---
title: "HTML 标记方法 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "anchor 方法 [JavaScript]"
  - "big 方法 [JavaScript]"
  - "blink 方法 [JavaScript]"
  - "bold 方法 [JavaScript]"
  - "fixed 方法 [JavaScript]"
  - "fontcolor 方法 [JavaScript]"
  - "fontsize 方法 [JavaScript]"
  - "HTML 标记方法 [JavaScript]"
  - "italics 方法 [JavaScript]"
  - "link 方法 [JavaScript]"
  - "small 方法 [JavaScript]"
  - "sub 方法 [JavaScript]"
  - "sup 方法 [JavaScript]"
ms.assetid: 50376223-be95-4aa4-9147-9e738a5d3cfa
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# HTML 标记方法 (JavaScript)
可使用 HTML 标记方法将 HTML 元素放置到 `String` 对象中的文本两侧。  
  
## 语法  
 下表列出了每个 HTML 标记方法的语法和说明。  
  
 在“语法”列中，`string1` 是 `String` 对象或文本。  
  
 “标准”列指示针对 HTML 4 的[万维网联合会 \(W3C\)](http://go.microsoft.com/fwlink/?LinkId=199553) 建议。  “不建议”指示为支持样式表而不建议使用 HTML 元素。  
  
|语法|方法说明|参数说明|标准|  
|--------|----------|----------|--------|  
|`string1`.anchor\(`name`\)|将具有 NAME 特性的 HTML 定位点放置到文本两侧。|`name` 参数是要置于 HTML 定位点的 NAME 特性中的文本。||  
|`string1`.big\(\)|将 HTML \<BIG\> 标记放置到文本两侧。||不建议|  
|`string1`.blink\(\)|将 HTML \<BLINK\> 标记放置到文本两侧。  Internet Explorer 中不支持 \<BLINK\> 标记。||非标准|  
|`string1`.bold\(\)|将 HTML \<B\> 标记放置到文本两侧。||不建议|  
|`string1`.fixed\(\)|将 HTML \<TT\> 标记放置到文本两侧。||不建议|  
|`string1`.fontcolor\(`color`\)|将具有 COLOR 特性的 HTML \<FONT\> 标记放置到文本两侧。|`color` 参数是包含十六进制值或预定义的颜色名称的字符串值。  有效的预定义颜色名称取决于 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 主机浏览器及其版本。|已弃用|  
|`string1`.fontsize\(`size`\)|将具有 SIZE 特性的 HTML \<FONT\> 标记放置到文本两侧。|`size` 参数是指定文本大小的整数值。  有效整数值取决于 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 主机浏览器及其版本。|已弃用|  
|`string1`.italics\(\)|将 HTML \<I\> 标记放置到文本两侧。||不建议|  
|`string1`.link\(`href`\)|将具有 HREF 特性的 HTML 定位点放置到文本两侧。|`href` 参数是要置于 HTML 定位点的 HREF 特性中的文本。||  
|`string1`.small\(\)|将 HTML \<SMALL\> 标记放置到文本两侧。||不建议|  
|`string1`.strike\(\)|将 HTML \<STRIKE\> 标记放置到文本两侧。||已弃用|  
|`string1`.sub\(\)|将 HTML \<SUB\> 标记放置到文本两侧。|||  
|`string1`.sup\(\)|将 HTML \<SUP\> 标记放置到文本两侧。|||  
  
## 备注  
 不执行用于确定 HTML 标记是否已应用于字符串的检查。  
  
## 示例  
 下面的示例演示如何使用 HTML 标记方法。  
  
```javascript  
// anchor method.  
var strVariable = "This is an anchor.";  
document.write(strVariable.anchor("Anchor1"));  
// Output: <A NAME="Anchor1">This is an anchor.</A>  
  
// big method.  
var strVariable = "This is a string.";  
document.write(strVariable.big());  
// Output: <BIG>This is a string.</BIG>  
  
//  blink method.  
var strVariable = "This is a string.";  
document.write(strVariable.blink());  
// Output: <BLINK>This is a string.</BLINK>  
  
//  bold method.  
var strVariable = "This is a string.";  
document.write(strVariable.bold());  
// Output: <B>This is a string.</B>  
  
//  fixed method.  
var strVariable = "This is a string.";  
document.write(strVariable.fixed());  
// Output: <TT>This is a string.</TT>  
  
//  fontcolor method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontcolor("red"));  
// Output: <FONT COLOR="red">This is a string.</FONT>  
  
//  fontsize method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontsize(-1));  
// Output: <FONT SIZE="-1">This is a string.</FONT>  
  
//  italics method  
var strVariable = "This is a string.";  
document.write(strVariable.italics());  
// Output: <I>This is a string.</I>  
  
//  link method.  
var strVariable = "This is a hyperlink.";  
document.write(strVariable.link("http://www.microsoft.com"));  
// Output: <A HREF="http://www.microsoft.com">This is a hyperlink.</A>  
  
//  small method.  
var strVariable = "This is a string.";  
document.write(strVariable.small());  
// Output: <SMALL>This is a string.</SMALL>  
  
//  strike method.  
var strVariable = "This is a string.";  
document.write(strVariable.strike());  
// Output: <STRIKE>This is a string.</STRIKE>  
  
//  sub method.  
var strVariable = "This is a string.";  
document.write(strVariable.sub());  
// Output: <SUB>This is a string.</SUB>  
  
//  sup method.  
var strVariable = "This is a string.";  
document.write(strVariable.sup());  
// Output: <SUP>This is a string.</SUP>  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**：[String 对象](../../javascript/reference/string-object-javascript.md)  
  
## 请参阅  
 [String 对象](../../javascript/reference/string-object-javascript.md)