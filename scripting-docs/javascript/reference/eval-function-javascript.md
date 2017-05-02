---
title: "eval 函数 (JavaScript) | Microsoft Docs"
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
  - "eval"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "eval 函数"
  - "解析，代码"
  - "分析器"
ms.assetid: 85587e39-9325-4b75-b9f9-9d7d475a2120
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# eval 函数 (JavaScript)
计算 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 代码并执行。  
  
## 语法  
  
```  
eval(codeString)   
```  
  
## 参数  
 `codeString`  
 必需。  包含有效 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 代码的 `String` 值。  
  
## 备注  
 利用 `eval` 函数，可动态执行 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 源代码。  
  
 `codeString` 字符串由 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 分析器分析并执行。  
  
 传递给 `eval` 函数的代码执行时所在的上下文和调用 `eval` 函数时的上下文一样。  
  
 尽量使用 [JSON.parse 函数](../../javascript/reference/json-parse-function-javascript.md)反序列化 JavaScript 对象表示法 \(JSON\) 文本。  `JSON.parse` 函数比 `eval` 函数更为安全且执行速度更快。  
  
## 示例  
 下面的代码将变量 `myDate` 初始化为一个测试日期。  
  
```javascript  
var dateFn = "Date(1971,3,8)";  
var myDate;  
eval("myDate = new " + dateFn + ";");  
  
document.write(myDate);  
  
// Output: Thu Apr 8 00:00:00 PDT 1971  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**：[Global 对象](../../javascript/reference/global-object-javascript.md)  
  
## 请参阅  
 [String 对象](../../javascript/reference/string-object-javascript.md)