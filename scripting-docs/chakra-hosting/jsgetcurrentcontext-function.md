---
title: "JsGetCurrentContext 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetCurrentContext"
helpviewer_keywords: 
  - "JsGetCurrentContext 函数"
ms.assetid: dd5fe0fa-d1e5-4af6-809e-e655a27519b5
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsGetCurrentContext 函数
获取线程上的当前脚本上下文。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsGetCurrentContext(  
   _Out_ JsContextRef *currentContext  
);  
```  
  
#### 参数  
 `currentContext`  
 如果没有当前脚本上下文，则线程上的当前脚本上下文为 NULL。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)