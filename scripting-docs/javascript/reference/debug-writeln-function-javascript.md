---
title: "Debug.writeln 函数 (JavaScript) | Microsoft Docs"
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
  - "writeln"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "writeIn 方法"
ms.assetid: c3aad0cd-0486-4161-9ba6-31d672da72af
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Debug.writeln 函数 (JavaScript)
将字符串发送到脚本调试器，后跟换行符。  
  
## 语法  
  
```  
  
Debug.writeln([str1 [, str2 [, ... [, strN]]]])  
```  
  
## 参数  
 *str1, str2, ..., strN*  
 可选。  要发送到脚本调试器的字符串。  
  
## 备注  
 `Debug.writeln` 函数在运行时将后跟换行符的字符串发送到 Microsoft 脚本调试器的即时窗口。  如果未调试脚本，则 `Debug.writeln` 函数不起作用。  
  
 `Debug.writeln` 函数与 `Debug.write` 函数几乎相同。  唯一的区别在于，`Debug.write` 函数不会在发送字符串后发送换行符。  
  
## 示例  
 此示例使用 `Debug.writeln` 函数在 Microsoft 脚本调试器的即时窗口中显示变量的值。  
  
> [!NOTE]
>  若要运行该示例，您必须已安装脚本调试器，并且脚本必须在调试模式下运行。  
>   
>  Internet Explorer 8 包含 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 调试器。  如果使用的是早期版本的 Internet Explorer，请参见[如何：从 Internet Explorer 中启用和启动脚本调试](http://go.microsoft.com/fwlink/?LinkId=133801)。  
  
```javascript  
var counter = 42;  
Debug.writeln("The value of counter is " + counter);  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[Debug 对象](../../javascript/reference/debug-object-javascript.md)  
  
## 请参阅  
 [Debug.write 函数](../../javascript/reference/debug-write-function-javascript.md)