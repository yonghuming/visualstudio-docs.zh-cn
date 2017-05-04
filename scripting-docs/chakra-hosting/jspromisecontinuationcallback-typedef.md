---
title: "JsPromiseContinuationCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 51a3fd02-9668-4cf7-bb0b-e1fd03b2528f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsPromiseContinuationCallback Typedef
承诺延续回调。  
  
## 语法  
  
```  
typedef void (CALLBACK *JsPromiseContinuationCallback)(  
  _In_ JsValueRef task,  
  _In_opt_ void *callbackState  
);  
```  
  
#### 参数  
 `task`  
  `callbackState`  
  
## 备注  
 主机可以在 `JsSetPromiseContinuationCallback` 中指定一个承诺延续回调。 如果脚本创建一个稍后要运行的任务，则承诺延续回调将随任务一起调用，且该任务将被放入 FIFO 队列，以便在当前脚本完成执行时运行。  
  
 此 API 仅在“边缘”模式下受到支持。  
  
## 要求  
 jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)