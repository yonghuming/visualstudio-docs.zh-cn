---
title: "JsRuntimeHandle Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 69e59bfd-9b0e-4710-9aa8-fbd6844171bc
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsRuntimeHandle Typedef
Chakra 运行时的句柄。  
  
## 语法  
  
```  
typedef void *JsRuntimeHandle;  
```  
  
## 备注  
 每个 Chakra 运行时都有自己独立的执行引擎、JIT 编译器和以及垃圾回收堆。  因此，每个运行时都完全独立于其他运行时。  
  
 运行时可在任意线程上使用，但任何时候只有一个线程能调入运行时。  
  
> [!WARNING]
>  与 Chakra 托管 API 中的其他对象引用不同，JsRuntimeHandle 不会作为垃圾回收，因为它本身包含垃圾回收堆。  运行时将继续存在，直到 JsDisposeRuntime 被调用。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)