---
title: "JsVariantToValue 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsVariantToValue"
helpviewer_keywords: 
  - "JsVariantToValue 函数"
ms.assetid: e8f9eb8b-55b3-4b65-927e-cad5b482edee
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsVariantToValue 函数
创建在 `VARIANT` 中传递的投影的 JavaScript 值。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsVariantToValue(  
   _In_ VARIANT *variant,  
   _Out_ JsValueRef *value  
);  
```  
  
#### 参数  
 `variant`  
 要投影的 `VARIANT`。  
  
 `value`  
 为 `VARIANT` 投影的 JavaScript 值。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 投影的值可以由脚本用于从脚本调用 COM 自动化对象。  主机负责强制实施 COM 线程处理规则。  
  
 需要活动脚本上下文。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)