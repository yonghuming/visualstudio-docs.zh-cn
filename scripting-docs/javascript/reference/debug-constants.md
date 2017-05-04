---
title: "调试常量 | Microsoft Docs"
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
ms.assetid: 76b572ee-bad0-404e-9fd4-841c9af35642
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# 调试常量
调试常量返回的常量值是 `Debug` 对象的属性。  
  
## Debug 对象常量  
 下表列出的常量值是 [Debug 对象](../../javascript/reference/debug-object-javascript.md)的属性。  
  
|常量|说明|值|  
|--------|--------|-------|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`|同步工作项分配了异步操作要运行的回调或延续。|0|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`|同步工作项符合部分联接异步操作。|1|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`|同步工作项符合选项异步操作。|2|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`|同步工作项已取消。|3|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`|同步工作项在异步操作中导致错误。|4|  
|`Debug.MS_ASYNC_OP_STATUS_SUCCESS`|异步操作成功。|1|  
|`Debug.MS_ASYNC_OP_STATUS_CANCELED`|异步操作已取消。|2|  
|`Debug.MS_ASYNC_OP_STATUS_ERROR`|异步操作导致错误。|3|  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 请参阅  
 [Debug.msTraceAsyncOperationCompleted 函数](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md)   
 [Debug.msUpdateAsyncCallbackRelation 函数](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md)