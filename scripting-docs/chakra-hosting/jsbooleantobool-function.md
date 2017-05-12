---
title: "JsBooleanToBool 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsBooleanToBool"
helpviewer_keywords: 
  - "JsBooleanToBool 函数"
ms.assetid: ab16ac71-fe47-475d-a7ee-46e4643dee60
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsBooleanToBool 函数
检索布尔值的 `bool` 值。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsBooleanToBool(  
   _In_ JsValueRef value,  
   _Out_ bool *boolValue  
);  
```  
  
#### 参数  
 `value`  
 要转换的值。  
  
 `boolValue`  
 转换后的值。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 需要活动脚本上下文。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)