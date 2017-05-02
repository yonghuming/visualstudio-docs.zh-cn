---
title: "debugger 语句 (JavaScript) | Microsoft Docs"
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
  - "debugger_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "debugger 语句"
ms.assetid: c6d2e193-c1f7-4fb3-8a4e-cc9823174ae4
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# debugger 语句 (JavaScript)
中止执行。  
  
## 语法  
  
```  
debugger  
```  
  
## 备注  
 可以将 `debugger` 语句放在过程的任何地方以中止执行。  使用 `debugger` 语句类似于在代码中设置断点。  
  
 `debugger` 语句中止执行，但它不关闭任何文件或清除任何变量。  
  
> [!NOTE]
>  除非正在调试脚本，否则 `debugger` 语句不起作用。  
  
## 示例  
 本示例使用 `debugger` 语句中止执行 `for` 循环里的每一次迭代。  
  
> [!NOTE]
>  若要运行该示例，您必须已安装脚本调试器，并且脚本必须在调试模式下运行。  
>   
>  Internet Explorer 8 包含 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 调试器。  如果使用的是早期版本的 Internet Explorer，请参见[如何：从 Internet Explorer 中启用和启动脚本调试](http://go.microsoft.com/fwlink/?LinkId=133801)。  
  
```javascript  
for(i = 1; i<5; i++) {  
   // Print i to the Output window.  
   Debug.write("loop index is " + i);  
   // Wait for user to resume.  
   debugger  
}  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 请参阅  
 [JavaScript 语句](../../javascript/reference/javascript-statements.md)   
 [条件编译](../../javascript/advanced/conditional-compilation-javascript.md)