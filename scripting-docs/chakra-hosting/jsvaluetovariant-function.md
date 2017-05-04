---
title: "JsValueToVariant 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsValueToVariant"
helpviewer_keywords: 
  - "JsValueToVariant 函数"
ms.assetid: 070244be-a69d-4b78-971b-69c0579c03cf
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsValueToVariant 函数
将传入的 `VARIANT` 初始化为 JavaScript 值的投影。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsValueToVariant(  
   _In_ JsValueRef object,  
   _Out_ VARIANT *variant  
);  
```  
  
#### 参数  
 `object`  
 项目的 `VARIANT` 形式的 JavaScript 值。  
  
 `variant`  
 一个指针，指向将初始化为投影的 `VARIANT` 结构。  
  
## 返回值  
  
## 备注  
 投影 `VARIANT` 可由 COM 自动化客户端用于调入投射的 JavaScript 对象。  
  
 需要活动脚本上下文。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)