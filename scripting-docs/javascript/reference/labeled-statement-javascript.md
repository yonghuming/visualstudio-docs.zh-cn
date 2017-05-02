---
title: "Labeled 语句 (JavaScript) | Microsoft Docs"
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
  - "labeled_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "continue 语句"
  - "标识符, 语句"
  - "标记语句"
ms.assetid: 019f898e-9e27-4be4-a22f-c5927c7fcae2
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Labeled 语句 (JavaScript)
为语句提供标识符。  
  
## 语法  
  
```  
  
      label :  
   statements   
```  
  
## 参数  
 *label*  
 必需。  在引用标记的语句时使用的唯一标识符。  
  
 `statements`  
 可选。  与 *label* 关联的一个或多个语句。  
  
## 备注  
 标签由 **break** 和 **continue** 语句用来指定要应用 **break** 和 **continue** 的语句。  
  
## 示例  
 在下面的代码中，**continue** 语句引用 `Inner:` 语句后面的 **for** 循环。  当 `j` 等于 24 时，**continue** 语句会导致该 **for** 循环转到下一迭代。  数字 21 到 23 以及 25 到 30 逐行显示。  
  
```javascript  
Outer:  
for (i = 1; i <= 10; i++) {  
   document.write ("<br />");  
   document.write ("i: " + i);  
   document.write (" j: ");  
  
Inner:  
   for (j = 21; j <= 30; j++) {  
      if (j == 24)  
          {  
          continue Inner;  
      }  
      document.write (j + " ");  
  }  
}  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 请参阅  
 [break 语句](../../javascript/reference/break-statement-javascript.md)   
 [continue 语句](../../javascript/reference/continue-statement-javascript.md)