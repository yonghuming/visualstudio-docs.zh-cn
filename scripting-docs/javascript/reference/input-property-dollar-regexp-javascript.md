---
title: "input 属性 ($_) (RegExp) (JavaScript) | Microsoft Docs"
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
  - "$_"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "$_ 属性"
  - "input 属性"
ms.assetid: 88c6d1d8-56f7-4334-a7eb-e899aec9cda4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# input 属性 ($_) (RegExp) (JavaScript)
返回执行正则表达式搜索所针对的字符串。  只读。  
  
## 语法  
  
```  
  
RegExp.input  
```  
  
## 备注  
 与此属性关联的对象始终为全局 `RegExp` 对象。  
  
 只要搜索字符串发生更改，就可以修改 **input** 属性的值。  
  
 下面的示例阐释了 **input** 属性的用法：  
  
```javascript  
function inputDemo(){  
   var s;  
   var re = new RegExp("d(b+)(d)","ig");  
   var str = "cdbBdbsbdbdz";  
   var arr = re.exec(str);  
   s = "The string used for the match was " + RegExp.input;   
   return(s);  
}  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[RegExp 对象](../../javascript/reference/regexp-object-javascript.md)  
  
## 请参阅  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-cn/ab0766e1-7037-45ed-aa23-706f58358c0e)