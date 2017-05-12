---
title: "JsGetRuntime 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetRuntime"
helpviewer_keywords: 
  - "JsGetRuntime 函数"
ms.assetid: 5b62e940-a885-405a-9fdd-0495fb391b95
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsGetRuntime 函数
获取上下文所属的运行时。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsGetRuntime(  
   _In_ JsContextRef context,  
   _Out_ JsRuntimeHandle *runtime  
);  
```  
  
#### 参数  
 `context`  
 从其中获取运行时的上下文。  
  
 `runtime`  
 上下文所属的运行时。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)