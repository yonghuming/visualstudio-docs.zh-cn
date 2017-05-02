---
title: "JsStopProfiling 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsStopProfiling"
helpviewer_keywords: 
  - "JsStopProfiling 函数"
ms.assetid: 3639c04f-a0f9-418b-be39-92f64b4e7ef8
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# JsStopProfiling 函数
停止在当前上下文中进行分析。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsStopProfiling(  
   _In_ HRESULT reason  
);  
```  
  
#### 参数  
 `reason`  
 停止分析以传递给探查器回调的原因。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 如果分析尚未启动，将不会返回错误。  
  
 需要活动脚本上下文。  
  
 桌面应用支持此 API，但应用商店应用不支持。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)