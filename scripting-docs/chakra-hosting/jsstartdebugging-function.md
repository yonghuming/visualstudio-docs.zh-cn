---
title: "JsStartDebugging 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsStartDebugging"
helpviewer_keywords: 
  - "JsStartDebugging 函数"
ms.assetid: c48ba02d-6d47-466f-a970-02f087d525f3
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# JsStartDebugging 函数
开始在当前上下文中调试。  
  
## 语法  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsStartDebugging();  
  
// Legacy mode signature  
STDAPI_(JsErrorCode)  JsStartDebugging(  
   _In_ IDebugApplication *debugApplication  
);  
```  
  
#### 参数  
 `debugApplication`  
 用于进行调试的调试应用程序。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 主机应确保在使用此 API 之前通过 `COINIT_MULTITHREADED` 或 `COINIT_APARTMENTTHREADED` 至少调用一次 `CoInitializeEx`。  
  
 在边缘模式下，`debugApplication` 参数不受支持。  有关在边缘模式下使用此 API 的详细信息，请参阅[针对 Edge 和旧引擎](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md)。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)