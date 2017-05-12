---
title: "JsGetProperty 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetProperty"
helpviewer_keywords: 
  - "JsGetProperty 函数"
ms.assetid: 606bc14f-e849-4f88-a148-6660e923c07b
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsGetProperty 函数
获取对象的属性。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsGetProperty(  
   _In_ JsValueRef object,  
   _In_ JsPropertyIdRef propertyId,  
   _Out_ JsValueRef *value  
);  
```  
  
#### 参数  
 `object`  
 包含属性的对象。  
  
 `propertyId`  
 属性的 ID。  
  
 `value`  
 该属性的值。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 需要活动脚本上下文。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)