---
title: "JsStartProfiling 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsStartProfiling"
helpviewer_keywords: 
  - "JsStartProfiling 函数"
ms.assetid: 638da395-42dd-4fc5-b581-819e647e887d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# JsStartProfiling 函数
开始在当前上下文中进行分析。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsStartProfiling(  
   _In_ IActiveScriptProfilerCallback *callback,  
   _In_ PROFILER_EVENT_MASK eventMask,  
   _In_ unsigned long context  
);  
```  
  
#### 参数  
 `callback`  
 要使用的分析回调。  
  
 `eventMask`  
 要用于进行回调的分析事件。  
  
 `context`  
 要传递给分析回调的上下文。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 需要活动脚本上下文。  
  
 桌面应用支持此 API，但应用商店应用不支持。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)