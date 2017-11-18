---
title: "Debug.msUpdateAsyncCallbackRelation 函数 |Microsoft 文档"
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
ms.assetid: ee6a1efc-375c-4ce8-a4e8-8896ee29f849
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c47ed7f6313646dddf86dd766d7f1027b2d38ad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="debugmsupdateasynccallbackrelation-function"></a>Debug.msUpdateAsyncCallbackRelation 函数
更新同步工作项和关联同步操作之间的关系状态。  
  
## <a name="syntax"></a>语法  
  
```  
Debug.msUpdateAsyncCallbackRelation(relatedAsyncOperationId, relationType)  
```  
  
#### <a name="parameters"></a>参数  
 `relatedAsyncOperationId`  
 必需。 与异步操作关联的 ID。  
  
 `relationType`  
 可选。 指定关系状态的值。  
  
## <a name="remarks"></a>备注  
 同步工作项通常是异步操作的回调函数。 当中止异步操作、使用联接操作或在其他情况下时，均可调用此函数。  
  
 `relationType` 可能的值包括：  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`  
  
 有关详细信息，请参阅[调试常量](../../javascript/reference/debug-constants.md)。  
  
> [!NOTE]
>  一些调试工具不显示通过此函数发送至调试器的信息。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]