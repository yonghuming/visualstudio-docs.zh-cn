---
title: "JsSetRuntimeMemoryLimit 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetRuntimeMemoryLimit"
helpviewer_keywords: 
  - "JsSetRuntimeMemoryLimit 函数"
ms.assetid: 74feb31f-19f6-43e3-b117-0694c59ac593
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSetRuntimeMemoryLimit 函数
设置运行时的当前内存限制。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryLimit(  
   _In_ JsRuntimeHandle runtime,  
   _In_ size_t memoryLimit  
);  
```  
  
#### 参数  
 `runtime`  
 将设置其内存限制的运行时。  
  
 `memoryLimit`  
 新的运行时内存限制（以字节为单位），或者 \-1 表示无内存限制。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 内存限制将导致超过限制的任何操作失败，出现“内存不足”错误。  将运行时的内存限制设置为 \-1 表示运行时无内存限制。  新的运行时默认为无内存限制。  如果新的内存限制超出当前使用量，则调用将成功，并且在此运行时中任何将来的分配都将失败，直到运行时的内存使用量低于该限制。  
  
 无论运行时是否在另一个线程上处于活动状态，始终都可以设置运行时的内存限制。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)