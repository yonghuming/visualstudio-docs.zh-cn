---
title: "JsRunSerializedScript 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsRunSerializedScript"
helpviewer_keywords: 
  - "JsRunSerializedScript 函数"
ms.assetid: 3fd3f6f1-eb3e-4751-92a5-c93b1035f3b2
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# JsRunSerializedScript 函数
运行序列化脚本。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsRunSerializedScript(  
   _In_z_ const wchar_t *script,  
   _In_ BYTE *buffer,  
   _In_ JsSourceContext sourceContext,  
   _In_z_ const wchar_t *sourceUrl,  
   _Out_ JsValueRef *result  
);  
```  
  
#### 参数  
 `script`  
 该序列化脚本的源代码。  
  
 `buffer`  
 序列化的脚本。  
  
 `sourceContext`  
 一个标识脚本的 Cookie，它可由可调试的脚本上下文使用。  
  
 `sourceUrl`  
 该脚本的来源位置。  
  
 `result`  
 运行该脚本的结果（如果有）。  此参数可以为 null。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 需要活动脚本上下文。  
  
 缓冲区不会通过脚本引擎保存在内存中，因此只要该缓冲区可能用于执行脚本，代码就必须让其处于活动状态。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)