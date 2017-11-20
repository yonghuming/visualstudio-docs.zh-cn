---
title: "调试常量 |Microsoft 文档"
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
ms.assetid: 76b572ee-bad0-404e-9fd4-841c9af35642
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2c50181dc9f40d8665d6caca407232231682d63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="debug-constants"></a>调试常量
调试常量返回的常量值是 `Debug` 对象的属性。  
  
## <a name="debug-object-constants"></a>Debug 对象常量  
 下表列出的常量值的属性[Debug 对象](../../javascript/reference/debug-object-javascript.md)。  
  
|返回的常量|描述|值|  
|--------------|-----------------|-----------|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`|同步工作项分配了异步操作要运行的回调或延续。|0|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`|同步工作项符合部分联接异步操作。|1|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`|同步工作项符合选项异步操作。|2|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`|同步工作项已取消。|3|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`|同步工作项在异步操作中导致错误。|4|  
|`Debug.MS_ASYNC_OP_STATUS_SUCCESS`|异步操作成功。|1|  
|`Debug.MS_ASYNC_OP_STATUS_CANCELED`|异步操作已取消。|2|  
|`Debug.MS_ASYNC_OP_STATUS_ERROR`|异步操作导致错误。|3|  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [Debug.msTraceAsyncOperationCompleted 函数](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md)   
 [Debug.msUpdateAsyncCallbackRelation 函数](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md)