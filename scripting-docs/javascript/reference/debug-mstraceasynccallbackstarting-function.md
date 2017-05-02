---
title: "Debug.msTraceAsyncCallbackStarting 函数 | Microsoft Docs"
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
ms.assetid: 0e2ca7c4-103c-44f2-b76c-102fb1e42543
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Debug.msTraceAsyncCallbackStarting 函数
将回调堆栈与之前指定的异步操作关联。  
  
## 语法  
  
```  
Debug.msTraceAsyncCallbackStarting(asyncOperationId)  
```  
  
#### 参数  
 `asyncOperationId`  
 必需。  与异步操作关联的 ID。  
  
## 备注  
 调用 `Debug.msTraceAsyncOperationCompleted` 后，调用异步操作的回调函数中的此函数。  
  
> [!NOTE]
>  一些调试工具不显示发送至调试器的信息。  
  
 `asyncOperationId` 必须与之前从 `Debug.msTraceAsyncOperationStarting` 返回的操作名称相对应。  
  
## 示例  
 以下代码提供了跟踪 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]应用的异步调用的示例。  
  
```javascript  
function asyncWrapperFunction() {  
    var opID = Debug.msTraceAsyncOperationStarting('async trace');  
    doSomethingAsync().then(function (result) {  
        Debug.msTraceAsyncOperationCompleted(opID, Debug.MS_ASYNC_OP_STATUS_SUCCESS);  
        Debug.msTraceAsyncCallbackStarting(opID);  
        // Process result of async operation.  
    }, function (error) {  
        Debug.msTraceAsyncOperationCompleted(opID, Debug.MS_ASYNC_OP_STATUS_ERROR);  
        Debug.msTraceAsyncCallbackStarting(opID);  
    });  
  
    Debug.msTraceAsyncCallbackCompleted();  
}  
  
function doSomethingAsync() {  
    return WinJS.Promise.as(true);  
}  
  
asyncWrapperFunction();  
```  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]