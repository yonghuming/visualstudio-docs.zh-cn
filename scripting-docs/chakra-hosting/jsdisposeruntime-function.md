---
title: "JsDisposeRuntime 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsDisposeRuntime"
helpviewer_keywords: 
  - "JsDisposeRuntime 函数"
ms.assetid: 0aefde3f-7250-48be-afc5-53ea85c12f30
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsDisposeRuntime 函数
释放运行时。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsDisposeRuntime(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### 参数  
 `runtime`  
 要释放的运行时。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 一旦释放了运行时，其拥有的所有资源将无效并无法使用。  如果运行时处于活跃状态（即  将其在特定线程上设置为最新），则不能释放该运行时。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)