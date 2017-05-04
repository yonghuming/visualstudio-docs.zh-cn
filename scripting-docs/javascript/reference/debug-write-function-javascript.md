---
title: "Debug.write 函数 (JavaScript) | Microsoft Docs"
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
  - "Write"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "write 方法 [JavaScript]"
ms.assetid: fd1cfbb3-46cb-47cc-896c-a70d457dd413
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# Debug.write 函数 (JavaScript)
将字符串发送到脚本调试器。  
  
## 语法  
  
```  
  
Debug.write([str1 [, str2 [, ... [, strN]]]])  
```  
  
## 参数  
 *str1, str2, ..., strN*  
 可选。  要发送到脚本调试器的字符串。  
  
## 备注  
 `Debug.write` 函数在运行时向脚本调试器的即时窗口发送字符串。  如果未调试脚本，则 `Debug.write` 函数不起作用。  
  
 `Debug.write` 函数与 `Debug.writeln` 函数几乎完全相同。  唯一的区别是 `Debug.writeln` 函数在发送字符串之后发送一个换行符。  
  
## 示例  
 此示例使用 `Debug.write` 函数在脚本调试器的即时窗口中显示变量值。  
  
> [!NOTE]
>  若要运行该示例，您必须已安装脚本调试器，并且脚本必须在调试模式下运行。  
>   
>  Internet Explorer 8 包含 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 调试器。  如果使用的是早期版本的 Internet Explorer，请参见[如何：从 Internet Explorer 中启用和启动脚本调试](http://go.microsoft.com/fwlink/?LinkId=133801)。  
  
```javascript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[Debug 对象](../../javascript/reference/debug-object-javascript.md)  
  
## 请参阅  
 [Debug.writeln 函数](../../javascript/reference/debug-writeln-function-javascript.md)