---
title: "JsSetProperty 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetProperty"
helpviewer_keywords: 
  - "JsSetProperty 函数"
ms.assetid: 2c36bebf-ec86-425c-8131-2dd75fd30f40
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSetProperty 函数
放入对象的属性。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsSetProperty(  
   _In_ JsValueRef object,  
   _In_ JsPropertyIdRef propertyId,  
   _In_ JsValueRef value,  
   _In_ bool useStrictRules  
);  
```  
  
#### 参数  
 `object`  
 包含属性的对象。  
  
 `propertyId`  
 属性的 ID。  
  
 `value`  
 属性的新值。  
  
 `useStrictRules`  
 属性集应遵循严格模式的规则。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 需要活动脚本上下文。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)