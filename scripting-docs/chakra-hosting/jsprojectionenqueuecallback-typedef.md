---
title: "JsProjectionEnqueueCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 19c1cefb-a7be-4196-b780-9fe6adf35ba5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# JsProjectionEnqueueCallback Typedef
当在原始线程以外的线程上完成投影 API 时，JsRT 调用的应用程序回调。  
  
## 语法  
  
```  
typedef void (CALLBACK *JsProjectionEnqueueCallback)(  
  _In_ JsProjectionCallback jsCallback,  
  _In_ JsProjectionCallbackContext jsContext,  
  _In_opt_ void *callbackState  
);  
```  
  
#### 参数  
 `jsCallback`  
 要在原始线程上调用的回调。  
  
 `jsContext`  
 应用程序上下文。  
  
 `callbackState`  
 必须传递到 `jsCallback` 的 JsRT 上下文。  
  
## 备注  
 需要调用 JsSetProjectionEnqueueCallback 才能接收回调。  
  
 此 API 仅在“边缘”模式下受到支持。  
  
## 要求  
 jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)