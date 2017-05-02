---
title: "条件（三元）运算符 (?:) (JavaScript) | Microsoft Docs"
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
  - "?:"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "条件（三元）运算符"
  - "条件运算符"
  - "三元"
ms.assetid: 7399ac32-9324-4a9a-ae76-be9c0f9df81c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# 条件（三元）运算符 (?:) (JavaScript)
视情况返回以下两个表达式之一。  
  
## 语法  
  
```  
  
test ? expression1 : expression2  
```  
  
## 参数  
 `test`  
 任何 Boolean 表达式。  
  
 `expression1`  
 如果 `test` 为 `true`，则返回表达式。  可能是逗号表达式。  
  
 `expression2`  
 如果 `test` 为 `false`，则返回表达式。  可以使用逗号表达式链接多个表达式。  
  
## 备注  
 `?:` 运算符可以用作 `if...else` 语句的快捷方式。  它通常用作较大表达式（使用 `if...else` 语句会很繁琐）的一部分。  例如：  
  
```javascript  
var now = new Date();  
var greeting = "Good" + ((now.getHours() > 17) ? " evening." : " day.");  
```  
  
 如果晚于下午 6 时，此示例将创建一个包含“Good evening.”的字符串。  使用 `if...else` 语句的等效代码如下：  
  
```javascript  
var now = new Date();  
var greeting = "Good";  
if (now.getHours() > 17)  
   greeting += " evening.";  
else  
   greeting += " day.";  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [if...else 语句](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)   
 [Script Junkie 配置小部件示例应用程序](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)