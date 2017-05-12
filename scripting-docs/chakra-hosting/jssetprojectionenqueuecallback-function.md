---
title: "JsSetProjectionEnqueueCallback 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: c751ccef-20d2-4d41-9568-1c54adf47cdf
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# JsSetProjectionEnqueueCallback 函数
设置要使用的回调，以便调将投影完成调回调用方所需线程。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsSetProjectionEnqueueCallback(  
   _In_ JsProjectionEnqueueCallback projectionEnqueueCallback,  
   _In_opt_ void *projectionEnqueueContext);  
  
```  
  
#### 参数  
 `projectionEnqueueContext`  
 无论何时背景线程上发生投影完成时将调用的回调。  
  
 `callbackState`  
 提供给 `projectionEnqueueContext` 的应用程序上下文。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 需要活动脚本上下文。  
  
 调用应来自不同的 COM 单元，或者来自相同 MTA 中的不同线程。  
  
 此 API 仅在“边缘”模式下受到支持。  
  
> [!CAUTION]
>  此 API 目前不支持 PInvoke。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)