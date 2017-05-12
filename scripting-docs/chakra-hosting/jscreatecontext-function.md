---
title: "JsCreateContext 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsCreateContext"
helpviewer_keywords: 
  - "JsCreateContext 函数"
ms.assetid: aceca043-2c73-4029-a06c-8ad6695109cf
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# JsCreateContext 函数
创建用于运行脚本的脚本上下文。  
  
## 语法  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsCreateContext(  
   _In_ JsRuntimeHandle runtime,  
   _Out_ JsContextRef *newContext);  
  
// Legacy mode signature  
STDAPI_(JsErrorCode) JsCreateContext(  
   _In_ JsRuntimeHandle runtime,  
   _In_ IDebugApplication *debugApplication,  
   _Out_ JsContextRef *newContext  
);  
```  
  
#### 参数  
 `runtime`  
 正在其中创建脚本上下文的运行时。  
  
 `debugApplication`  
 用于进行调试的调试应用程序。  此参数可为 NULL，在这种情况下，没有为上下文启用调试。  
  
 `newContext`  
 创建的脚本上下文。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 每个脚本上下文都具有其自己的全局对象，该对象独立于所有其他脚本上下文。  
  
 在边缘模式下，`debugApplication` 参数不受支持。  有关在边缘模式下使用此 API 的详细信息，请参阅[针对 Edge 和旧引擎](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md)。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)