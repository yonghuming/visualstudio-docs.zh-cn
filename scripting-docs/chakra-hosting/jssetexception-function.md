---
title: "JsSetException 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetException"
helpviewer_keywords: 
  - "JsSetException 函数"
ms.assetid: c528793a-2e1b-4ee1-bd2e-e63fd547dc40
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSetException 函数
将当前上下文的运行时设置为异常状态。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsSetException(  
   _In_ JsValueRef exception  
);  
```  
  
#### 参数  
 `exception`  
 要为当前上下文的运行时设置的 JavaScript 异常。  
  
## 返回值  
 如果引擎设置为异常状态，则返回 `JsNoError`；否则返回失败代码。  
  
## 备注  
 如果当前上下文的运行时已处于异常状态，此 API 将返回 `JsErrorInExceptionState`。  
  
 需要活动脚本上下文。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)