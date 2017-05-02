---
title: "JsProjectionCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 32f22d37-e57e-4196-b6cd-a3fc75bd0632
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsProjectionCallback Typedef
应使用正确线程中传递到 `JsProjectionEnqueueCallback` 的上下文调用 JsRT 回调。  
  
## 语法  
  
```  
typedef void (CALLBACK *JsProjectionCallback)(  
  _In_ JsProjectionCallbackContext jsContext  
);  
```  
  
#### 参数  
 `jsContext`  
 需要调用 `JsSetProjectionEnqueueCallback` 以接收回调。  
  
## 备注  
 此 API 仅在“边缘”模式下受到支持。  
  
## 要求  
 jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)