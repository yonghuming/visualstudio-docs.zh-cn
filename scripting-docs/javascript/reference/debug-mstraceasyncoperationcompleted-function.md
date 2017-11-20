---
title: "Debug.msTraceAsyncOperationCompleted 函数 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 9b628b71-61f1-478a-857f-5e1f607db56c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41370257042a2de50d21eba51c299198a6bfb72a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="debugmstraceasyncoperationcompleted-function"></a>Debug.msTraceAsyncOperationCompleted 函数
指示异步操作已完成。  
  
## <a name="syntax"></a>语法  
  
```  
Debug.msTraceAsyncOperationCompleted(asyncOperationId, status)  
```  
  
#### <a name="parameters"></a>参数  
 `asyncOperationId`  
 必需。 与异步操作关联的 ID。  
  
 `status`  
 可选。 异步操作的状态。 如果未指定，则使用 `Debug.MS_ASYNC_OP_STATUS_SUCCESS`。  
  
## <a name="remarks"></a>备注  
 在异步操作完成时调用该函数。  
  
 `asyncOperationId` 必须与之前从 `Debug.msTraceAsyncOperationStarting` 返回的操作 ID 相对应。  
  
 `status` 可能的值包括：  
  
-   `Debug.MS_ASYNC_OP_STATUS_SUCCESS`  
  
-   `Debug.MS_ASYNC_OP_STATUS_CANCELED`  
  
-   `Debug.MS_ASYNC_OP_STATUS_ERROR`  
  
> [!NOTE]
>  一些调试工具不显示发送至调试器的信息。  
  
## <a name="example"></a>示例  
 以下代码提供了跟踪 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]应用的异步调用的示例。  
  
```JavaScript  
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
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]