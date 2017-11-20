---
title: "Debug.msTraceAsyncOperationStarting 函数 |Microsoft 文档"
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
ms.assetid: c8458264-07e0-4cd6-8528-ff7cf009cf9e
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a50c58e352d40a06192664cdf7424348be02d466
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="debugmstraceasyncoperationstarting-function"></a>Debug.msTraceAsyncOperationStarting 函数
启动对异步操作的跟踪。  
  
## <a name="syntax"></a>语法  
  
```  
Debug.msTraceAsyncOperationStarting(operationName)  
```  
  
#### <a name="parameters"></a>参数  
 `operationName`  
 必需。 一个标识异步操作的字符串。 如果 `operationName` 为 null 或未定义，操作名称将采用空字符串。  
  
## <a name="return-value"></a>返回值  
 一个表示操作 ID 的整数。  
  
## <a name="remarks"></a>备注  
 在异步操作开始前调用该方法。  
  
> [!NOTE]
>  一些调试工具不显示发送至调试器的信息。  
  
## <a name="example"></a>示例  
 以下代码提供检测 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]应用的异步调用示例。  
  
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