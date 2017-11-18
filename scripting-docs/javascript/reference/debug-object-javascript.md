---
title: "Debug 对象 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: debug
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Debug object
- Debug object, about Debug object
ms.assetid: 42a367ec-beb1-4e59-8342-34c326eca042
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6286e5db853daa97e43f36a1467abe90cbced5c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="debug-object-javascript"></a>Debug 对象 (JavaScript)
它是将输出发送到调试器的内部全局对象。  
  
## <a name="syntax"></a>语法  
  
```  
Debug.function  
```  
  
## <a name="remarks"></a>备注  
 不需要实例化 Debug 对象。 可以通过调用 `function`访问其所有属性和方法。  
  
 调试 Internet Explorer 和 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 应用的方式有所不同。 在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 应用中， `write` 对象的 `writeln` 和 `Debug` 函数在运行时在 Visual Studio 的“输出”窗口  中显示字符串。 有关调试的详细信息[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]应用程序，请参阅[调试 Windows 通用应用在 Visual Studio 中](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps.md)。  
  
 若要调试 Internet Explorer 脚本，必须安装有脚本调试器且必须在调试模式下运行脚本。 Internet Explorer 8 及更高版本包括 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 调试器。 如果使用的是 Internet Explorer 的早期版本，请参阅 [如何：从 Internet Explorer 启用和启动脚本调试](http://go.microsoft.com/fwlink/?LinkId=133801)。  
  
 如果不调试脚本，这些函数将不起作用。  
  
## <a name="example"></a>示例  
 此示例使用 `write` 函数来显示变量的值。  
  
```JavaScript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="constants"></a>常量  
 [Debug 常量](../../javascript/reference/debug-constants.md)  
  
## <a name="properties"></a>属性  
 [Debug.debuggerEnabled 属性](../../javascript/reference/debug-debuggerenabled-property.md)&#124;[Debug.setNonUserCodeExceptions 属性](../../javascript/reference/debug-setnonusercodeexceptions-property.md)  
  
## <a name="functions"></a>函数  
 [Debug.msTraceAsyncCallbackStarting 函数](../../javascript/reference/debug-mstraceasynccallbackstarting-function.md)&#124;[Debug.msTraceAsyncCallbackCompleted 函数](../../javascript/reference/debug-mstraceasynccallbackcompleted-function.md)&#124;[Debug.msTraceAsyncOperationCompleted 函数](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md)&#124;[Debug.msTraceAsyncOperationStarting 函数](../../javascript/reference/debug-mstraceasyncoperationstarting-function.md)&#124;[Debug.msUpdateAsyncCallbackRelation 函数](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md)&#124;[Debug.write 函数](../../javascript/reference/debug-write-function-javascript.md)&#124;[Debug.writeln 函数](../../javascript/reference/debug-writeln-function-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [debugger 语句](../../javascript/reference/debugger-statement-javascript.md)