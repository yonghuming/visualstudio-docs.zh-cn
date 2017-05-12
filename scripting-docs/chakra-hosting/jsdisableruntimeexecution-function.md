---
title: "JsDisableRuntimeExecution 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsDisableRuntimeExecution"
helpviewer_keywords: 
  - "JsDisableRuntimeExecution 函数"
ms.assetid: 4bd4670a-a9da-4f8c-b3fd-1fd366d915c3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsDisableRuntimeExecution 函数
挂起脚本执行，并终止运行时中正在运行的任何脚本。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsDisableRuntimeExecution(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### 参数  
 `runtime`  
 要挂起的运行时。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 调用 `JsEnableRuntimeExecution` 之前，无法调用挂起的运行时。  
  
 不必在运行时处于活动状态的线程上调用此 API。  尽管运行时将进入挂起状态，但正在执行的脚本可能不会立即挂起；而正在运行的脚本将尽快终止并引发不可捕获的异常。  
  
 在已挂起的运行时中挂起执行是一个空操作。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)