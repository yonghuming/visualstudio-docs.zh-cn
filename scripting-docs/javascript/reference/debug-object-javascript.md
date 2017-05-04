---
title: "Debug 对象 (JavaScript) | Microsoft Docs"
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
  - "debug"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Debug 对象"
  - "Debug 对象, 关于 Debug 对象"
ms.assetid: 42a367ec-beb1-4e59-8342-34c326eca042
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Debug 对象 (JavaScript)
它是将输出发送到调试器的内部全局对象。  
  
## 语法  
  
```  
Debug.function  
```  
  
## 备注  
 不需要实例化 Debug 对象。 可以通过调用 `function` 访问其所有属性和方法。  
  
 调试 Internet Explorer 和 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 应用的方式有所不同。 在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 应用中，`Debug` 对象的 `write` 和 `writeln` 函数在运行时在 Visual Studio 的“输出”窗口中显示字符串。 有关调试 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 应用的详细信息，请参阅[在 Visual Studio 中调试应用程序](~/debugger/debug-store-apps-in-visual-studio.md)。  
  
 若要调试 Internet Explorer 脚本，必须安装有脚本调试器且必须在调试模式下运行脚本。 Internet Explorer 8 及更高版本包括 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 调试器。 如果使用的是 Internet Explorer 的早期版本，请参阅[如何：从 Internet Explorer 启用和启动脚本调试](http://go.microsoft.com/fwlink/?LinkId=133801)。  
  
 如果不调试脚本，这些函数将不起作用。  
  
## 示例  
 此示例使用 `write` 函数来显示变量的值。  
  
```javascript  
var counter = 42; Debug.write("The value of counter is " + counter);  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 常量  
 [调试常量](../../javascript/reference/debug-constants.md)  
  
## 属性  
 [Debug.debuggerEnabled 属性](../../javascript/reference/debug-debuggerenabled-property.md) &#124; [Debug.setNonUserCodeExceptions 属性](../../javascript/reference/debug-setnonusercodeexceptions-property.md)  
  
## 函数  
 [Debug.msTraceAsyncCallbackStarting 函数](../../javascript/reference/debug-mstraceasynccallbackstarting-function.md) &#124; [Debug.msTraceAsyncCallbackCompleted 函数](../../javascript/reference/debug-mstraceasynccallbackcompleted-function.md) &#124; [Debug.msTraceAsyncOperationCompleted 函数](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md) &#124; [Debug.msTraceAsyncOperationStarting 函数](../../javascript/reference/debug-mstraceasyncoperationstarting-function.md) &#124; [Debug.msUpdateAsyncCallbackRelation 函数](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md) &#124; [Debug.write 函数](../../javascript/reference/debug-write-function-javascript.md) &#124; [Debug.writeln 函数](../../javascript/reference/debug-writeln-function-javascript.md)  
  
## 请参阅  
 [debugger 语句](../../javascript/reference/debugger-statement-javascript.md)