---
title: "JsGetValueType 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetValueType"
helpviewer_keywords: 
  - "JsGetValueType 函数"
ms.assetid: f403cf7c-c8c0-4a17-bfa9-0302d00e760e
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsGetValueType 函数
获取 JsValueRef 的 JavaScript 类型。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsGetValueType(  
   _In_ JsValueRef value,  
   _Out_ JsValueType *type  
);  
```  
  
#### 参数  
 `value`  
 要返回其类型的值。  
  
 `type`  
 值的类型。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 需要活动脚本上下文。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)