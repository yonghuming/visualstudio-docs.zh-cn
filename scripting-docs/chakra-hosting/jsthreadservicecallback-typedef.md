---
title: "JsThreadServiceCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: dbe67be5-418a-4f66-8b68-b38078a6d140
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsThreadServiceCallback Typedef
线程服务回调。  
  
## 语法  
  
```  
typedef bool (CALLBACK *JsThreadServiceCallback)(  
   _In_ JsBackgroundWorkItemCallback callback,  
   _In_opt_ void *callbackData  
);  
```  
  
#### 参数  
 回调  
 用于后台工作项的回调。  
  
 callbackData  
 要传递给回调的数据参数。  
  
## 备注  
 当调用 JsCreateRuntime 时，主机可以指定后台线程服务。  若已指定，则使用此回调将后台工作项传递给该主机。  主机应立即开始执行后台工作项并返回 true，或者返回 false，且运行时将在线程中处理工作项。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)