---
title: "JsBoolToBoolean 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsBoolToBoolean"
helpviewer_keywords: 
  - "JsBoolToBoolean 函数"
ms.assetid: 24322ea3-0638-40a3-9b4c-fc912ebed3ff
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsBoolToBoolean 函数
从 `bool` 值中创建布尔值。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode JsBoolToBoolean(  
   _In_ bool value,  
   _Out_ JsValueRef *booleanValue  
);  
```  
  
#### 参数  
 `value`  
 要转换的值。  
  
 `booleanValue`  
 转换后的值。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 需要活动脚本上下文。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)