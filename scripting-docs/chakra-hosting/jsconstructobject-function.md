---
title: "JsConstructObject 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsConstructObject"
helpviewer_keywords: 
  - "JsConstructObject 函数"
ms.assetid: b07d2440-db55-4a6a-8376-56b40a8039a1
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsConstructObject 函数
将函数作为构造函数调用。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsConstructObject(  
   _In_ JsValueRef function,  
   _In_reads_(argumentCount) JsValueRef *arguments,  
   _In_ unsigned short argumentCount,  
   _Out_opt_ JsValueRef *result  
);  
```  
  
#### 参数  
 `function`  
 要作为构造函数调用的函数。  
  
 `arguments`  
 调用的参数。  
  
 `argumentCount`  
 正在传递给函数的参数数目。  
  
 `result`  
 从函数调用返回的值。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 需要活动脚本上下文。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)