---
title: "JsSetRuntimeBeforeCollectCallback 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetRuntimeBeforeCollectCallback"
helpviewer_keywords: 
  - "JsSetRuntimeBeforeCollectCallback 函数"
ms.assetid: 7b2fb911-6007-4ed9-a307-66cefe590ea4
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSetRuntimeBeforeCollectCallback 函数
设置在垃圾回收之前由运行时调用的回调函数。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeBeforeCollectCallback(  
   _In_ JsRuntimeHandle runtime,  
   _In_opt_ void *callbackState,  
   _In_ JsBeforeCollectCallback beforeCollectCallback  
);  
```  
  
#### 参数  
 `runtime`  
 为其注册分配回调的运行时。  
  
 `callbackState`  
 将传回到回调的用户提供状态。  
  
 `beforeCollectCallback`  
 要设置的回调函数。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 在当前运行时执行线程上调用回调，因此在回调完成前将阻止执行。  
  
 主机可使用该回调来准备垃圾回收。  例如，通过释放 Chakra 对象上不必要的引用。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)