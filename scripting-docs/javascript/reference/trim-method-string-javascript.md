---
title: "trim 方法 (String) (JavaScript) | Microsoft Docs"
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
  - "trim 方法"
ms.assetid: 03d38c7e-25cd-4ede-b58e-1a10b5249bab
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# trim 方法 (String) (JavaScript)
从字符串中移除前导空格、尾随空格和行终止符。  
  
## 语法  
  
```  
  
stringObj.trim()  
```  
  
## 参数  
 `stringObj`  
 必选。  `String` 对象或字符串。  `trim` 方法不修改该字符串。  
  
## 返回值  
 已移除前导空格、尾随空格和行终止符的原始字符串。  
  
## 备注  
 移除的字符包括空格、制表符、换页符、回车符和换行符。  有关空格和行终止符的完整列表，请参见[特殊字符](../../javascript/advanced/special-characters-javascript.md)。  
  
 有关说明如何实现你自己的修整方法的示例，请参见[原型和原型继承](../../javascript/advanced/prototypes-and-prototype-inheritance.md)。  
  
## 示例  
 下面的示例演示 `trim` 方法的用法。  
  
```javascript  
var message = "    abc def     \r\n  ";  
  
document.write("[" + message.trim() + "]");  
document.write("<br/>");  
document.write("length: " + message.trim().length);  
  
// Output:  
//  [abc def]  
//  length: 7  
```  
  
## 要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 请参阅  
 [特殊字符](../../javascript/advanced/special-characters-javascript.md)   
 [String 对象](../../javascript/reference/string-object-javascript.md)   
 [滚动、平移和缩放示例应用程序](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)