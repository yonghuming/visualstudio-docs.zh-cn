---
title: "JsCollectGarbage 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsCollectGarbage"
helpviewer_keywords: 
  - "JsCollectGarbage 函数"
ms.assetid: 995c79a5-6e18-45be-81ff-2a5d3348edb8
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsCollectGarbage 函数
执行完全垃圾回收。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsCollectGarbage(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### 参数  
 `runtime`  
 将在其中执行垃圾回收的运行时。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)