---
title: "Debug.msTraceAsyncCallbackStarting 函数 |Microsoft 文档"
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
ms.assetid: 0e2ca7c4-103c-44f2-b76c-102fb1e42543
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49203cdf16e7cbd74493c882d9cf17b7629da79a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="debugmstraceasynccallbackstarting-function"></a>Debug.msTraceAsyncCallbackStarting 函数
将回调堆栈与之前指定的异步操作关联。  
  
## <a name="syntax"></a>语法  
  
```  
Debug.msTraceAsyncCallbackStarting(asyncOperationId)  
```  
  
#### <a name="parameters"></a>参数  
 `asyncOperationId`  
 必需。 与异步操作关联的 ID。  
  
## <a name="remarks"></a>备注  
 调用 `Debug.msTraceAsyncOperationCompleted` 后，调用异步操作的回调函数中的此函数。  
  
> [!NOTE]
>  一些调试工具不显示发送至调试器的信息。  
  
 `asyncOperationId` 必须与之前从 `Debug.msTraceAsyncOperationStarting` 返回的操作名称相对应。  
  
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