---
title: "JsBeforeCollectCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 58bece47-4e6d-49e7-a93d-b6a8f9928b41
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsBeforeCollectCallback Typedef
在收集之前调用的回调。  
  
## 语法  
  
```  
typedef void (CALLBACK *JsBeforeCollectCallback)(  
_In_opt_ void *callbackState  
);  
```  
  
#### 参数  
 callbackState  
 传递到 JsSetBeforeCollectCallback 的状态。  
  
## 备注  
 使用 JsSetBeforeCollectCallback 注册此回调。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)