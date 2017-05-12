---
title: "JsSetCurrentContext 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetCurrentContext"
helpviewer_keywords: 
  - "JsSetCurrentContext 函数"
ms.assetid: 603cc94c-6585-411b-89f9-c6f144e2aa30
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSetCurrentContext 函数
在线程上设置当前脚本上下文。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsSetCurrentContext(  
   _In_ JsContextRef context  
);  
```  
  
#### 参数  
 `context`  
 要设置为当前脚本上下文的脚本上下文。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)