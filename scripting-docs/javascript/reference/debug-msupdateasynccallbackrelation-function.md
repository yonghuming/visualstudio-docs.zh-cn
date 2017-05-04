---
title: "Debug.msUpdateAsyncCallbackRelation 函数 | Microsoft Docs"
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
ms.assetid: ee6a1efc-375c-4ce8-a4e8-8896ee29f849
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Debug.msUpdateAsyncCallbackRelation 函数
更新同步工作项和关联同步操作之间的关系状态。  
  
## 语法  
  
```  
Debug.msUpdateAsyncCallbackRelation(relatedAsyncOperationId, relationType)  
```  
  
#### 参数  
 `relatedAsyncOperationId`  
 必需。  与异步操作关联的 ID。  
  
 `relationType`  
 可选。  指定关系状态的值。  
  
## 备注  
 同步工作项通常是异步操作的回调函数。  当中止异步操作、使用联接操作或在其他情况下时，均可调用此函数。  
  
 `relationType` 可能的值包括：  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`  
  
 有关更多信息，请参见[调试常量](../../javascript/reference/debug-constants.md)。  
  
> [!NOTE]
>  一些调试工具不显示通过此函数发送至调试器的信息。  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]