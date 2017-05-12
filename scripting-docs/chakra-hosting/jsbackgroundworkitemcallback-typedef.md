---
title: "JsBackgroundWorkItemCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: e6db52e1-830c-46a2-b9f9-cc2d450a1da8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsBackgroundWorkItemCallback Typedef
后台工作项回调。  
  
## 语法  
  
```  
typedef void (CALLBACK *JsBackgroundWorkItemCallback)(  
   _In_opt_ void *callbackData  
);  
```  
  
#### 参数  
 callbackData  
 传递到线程服务的数据参数。  
  
## 备注  
 这将传递到主机的线程服务（如果提供），它使该主机可在其选择的后台线程上调用工作项回调。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)