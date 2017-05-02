---
title: "JavaScriptlastParen 属性 ($+) (RegExp) (JavaScript) | Microsoft Docs"
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
  - "$+"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lastParen 属性 ($+)"
ms.assetid: 18aca591-a97a-48da-8b06-422346804b16
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JavaScriptlastParen 属性 ($+) (RegExp) (JavaScript)
从任何正则表达式搜索中返回最后一个带括号的子匹配项（如果有）。  只读。  
  
## 语法  
  
```  
  
RegExp.lastParen  
```  
  
## 备注  
 与此属性关联的对象始终为全局 `RegExp` 对象。  
  
 `lastParen` 属性的初始值是空字符串。  每当产生成功匹配时，`lastParen` 属性的值就会相应更改。  
  
## 示例  
 下面的示例阐释了 `lastParen` 属性的用法：  
  
```javascript  
// Create the regular expression pattern.  
var re = new RegExp("d(b+)(d)","ig");  
var str = "cdbBdbsbdbdz";  
  
// Perform the search.  
var arr = re.exec(str);  
  
// Print the output.  
var s = ""   
s += "$1: " + RegExp.$1 + "<br />";  
s += "$2: " + RegExp.$2 + "<br />";  
s += "$3: " + RegExp.$3 + "<br />";  
s += "input: " + RegExp.input + "<br />";  
s += "lastMatch: " + RegExp.lastMatch + "<br />";  
s += "leftContext: " + RegExp.leftContext + "<br />";  
s += "rightContext: " + RegExp.rightContext + "<br />";   
s += "lastParen: " + RegExp.lastParen + "<br />";  
  
document.write(s);  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**：[RegExp 对象](../../javascript/reference/regexp-object-javascript.md)  
  
## 请参阅  
 [$1...$9 属性 \(RegExp\)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)   
 [index 属性 \(RegExp\)](../../javascript/reference/index-property-regexp-javascript.md)   
 [input 属性 \($\_\) \(RegExp\)](../../javascript/reference/input-property-dollar-regexp-javascript.md)   
 [lastIndex 属性 \(RegExp\)](../../javascript/reference/lastindex-property-regexp-javascript.md)   
 [lastMatch 属性 \($&\) \(RegExp\)](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)   
 [leftContext 属性 \($\`\) \(RegExp\)](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)   
 [rightContext 属性 \($'\) \(RegExp\)](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)