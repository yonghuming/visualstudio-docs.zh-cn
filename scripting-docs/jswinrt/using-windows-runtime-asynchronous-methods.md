---
title: "使用 Windows 运行时异步方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, Windows 运行时异步方法"
ms.assetid: 70756833-44f7-4383-827f-2ac781558082
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# 使用 Windows 运行时异步方法
许多 Windows 运行时方法（特别是可能需要花费很长时间才能完成的方法）是异步的。  这些方法通常返回一个异步行为或操作（例如，`Windows.Foundation.IAsyncAction`、`Windows.Foundation.IAsyncOperation`、`Windows.Foundation.IAsyncActionWithProgress` 或 `Windows.Foundation.IAsyncOperationWithProgress`）。  这些方法在 JavaScript 中由 [CommonJS\/Promises\/A](http://go.microsoft.com/fwlink/p/?LinkId=244434) 模式表示。  也就是说，它们返回一个具有 [then](http://msdn.microsoft.com/zh-cn/c63904fc-465b-4fd5-a1d6-e4fb200248e7) 函数的 Promise 对象，你必须为其提供一个 `completed` 函数（如果操作成功，则该函数将处理结果）。  如果你不希望提供错误处理程序，则应使用 [done](http://msdn.microsoft.com/zh-cn/9a5e6877-a2cf-421f-a91e-37d84ccb40da) 函数而不是 [then](http://msdn.microsoft.com/zh-cn/c63904fc-465b-4fd5-a1d6-e4fb200248e7) 函数。  
  
> [!IMPORTANT]
>  Windows 运行时功能不适用于在 Internet Explorer 中运行的应用。  
  
## 异步方法的示例  
 在以下示例中，[then](http://msdn.microsoft.com/zh-cn/c63904fc-465b-4fd5-a1d6-e4fb200248e7) 函数采用表示 `createResourceAsync` 方法的完成值的参数。  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
        console.log("New item is: " + newItem.id);  
            });  
```  
  
 在这种情况下，如果 `createResourceAsync` 方法失败，则它以错误状态返回一个承诺，但不会引发异常。  你可以通过使用如下所示的 [then](http://msdn.microsoft.com/zh-cn/c63904fc-465b-4fd5-a1d6-e4fb200248e7) 函数处理错误。  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
              console.log("New item is: " + newItem.id);  
          }  
          function(err) {  
              console.log("Got error: " + err.message);  
          });  
```  
  
 如果你不想以显式方式处理错误，但希望它引发异常，则你可以改用 [done](http://msdn.microsoft.com/zh-cn/9a5e6877-a2cf-421f-a91e-37d84ccb40da) 函数。  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .done(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            });  
```  
  
 你也可以通过使用第三个函数显示完成的进度。  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .then(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            },  
    // Error.  
            function(error) {   
               alert("Failed to create a resource.");  
            },  
    // Progress.  
            function(progress, resultSoFar) {   
               setProgressBar(progress);  
            });  
```  
  
 有关异步编程的详细信息，请参阅[Asynchronous programming](http://msdn.microsoft.com/zh-cn/904ff97c-bb36-4ac5-9eda-a961e3639415)。  
  
## 请参阅  
 [在 JavaScript 中使用 Windows 运行时](../jswinrt/using-the-windows-runtime-in-javascript.md)