---
title: "JsEquals 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsEquals"
helpviewer_keywords: 
  - "JsEquals 函数"
ms.assetid: 8377a7b6-12ff-43e4-8cc8-5a5a198a168b
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsEquals 函数
比较两个 JavaScript 值是否相等。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsEquals(  
   _In_ JsValueRef object1,  
   _In_ JsValueRef object2,  
   _Out_ bool *result  
);  
```  
  
#### 参数  
 `object1`  
 要比较的第一个对象。  
  
 `object2`  
 要比较的第二个对象。  
  
 `result`  
 值是否相等。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 此函数等效于 Javascript 中的 `==` 运算符。  
  
 需要活动脚本上下文。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)