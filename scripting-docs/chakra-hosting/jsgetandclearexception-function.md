---
title: "JsGetAndClearException 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetAndClearException"
helpviewer_keywords: 
  - "JsGetAndClearException 函数"
ms.assetid: 6aec8a88-41ee-47f6-b5f4-32f3cae6bb7b
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsGetAndClearException 函数
返回导致当前上下文的运行时处于异常状态的异常，并重置该运行时的异常状态。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsGetAndClearException(  
   _Out_ JsValueRef *exception  
);  
```  
  
#### 参数  
 `exception`  
 当前上下文运行时的异常。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 如果当前上下文的运行时不处于异常状态，此 API 将返回 `JsErrorInvalidArgument`。  如果禁用了运行时，这将返回一个异常，指示已终止该脚本，但它不会清除异常（如果使用 `JsEnableRuntimeExecution` 重新启用了运行时，则将清除异常）。  
  
 需要活动脚本上下文。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)