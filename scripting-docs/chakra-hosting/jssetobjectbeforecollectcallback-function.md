---
title: "JsSetObjectBeforeCollectCallback 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: ea2cbd94-d8b0-4fa9-a4a1-c75a4e338eaf
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsSetObjectBeforeCollectCallback 函数
设置在对象的垃圾回收之前由运行时调用的回调函数。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsSetObjectBeforeCollectCallback(  
   _In_ JsRef ref,  
   _In_opt_ void *callbackState,  
   _In_ JsObjectBeforeCollectCallback objectBeforeCollectCallback  
);  
```  
  
#### 参数  
 `ref`  
 要为其注册回调的对象。  
  
 `callbackState`  
 将要传递回回调的用户提供的状态。  
  
 `objectBeforeCollectCallback`  
 要设置的回调函数。  使用 null 清除之前注册的回调。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 由于回调在当前运行时执行线程上调用，因此在回调完成前将阻止执行。  
  
 此 API 仅在“边缘”模式下受到支持。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)