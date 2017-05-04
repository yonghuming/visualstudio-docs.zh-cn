---
title: "JsProjectionCallbackContext Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 50c705c5-664f-4a1a-92f6-4882fc718ab1
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsProjectionCallbackContext Typedef
上下文从 JsRT 传递到应用程序回调 JsProjectionEnqueueCallback，然后通过正确线程上的应用程序回传给提供的回调 `JsProjectionCallback` 中的 JsRT。  
  
## 语法  
  
```cpp  
typedef void *JsProjectionCallbackContext;  
```  
  
## 备注  
 需要调用 `JsSetProjectionEnqueueCallback` 以接收回调。  
  
 此 API 仅在“边缘”模式下受到支持。  
  
## 要求  
 jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)