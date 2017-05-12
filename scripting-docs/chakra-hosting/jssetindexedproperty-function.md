---
title: "JsSetIndexedProperty 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetIndexedProperty"
helpviewer_keywords: 
  - "JsSetIndexedProperty 函数"
ms.assetid: ccbc5bf4-d99b-485c-ab25-d2bd1ed2142e
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSetIndexedProperty 函数
设置对象指定索引处的值。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsSetIndexedProperty(  
   _In_ JsValueRef object,  
   _In_ JsValueRef index,  
   _In_ JsValueRef value  
);  
```  
  
#### 参数  
 `object`  
 要对其执行操作的对象。  
  
 `index`  
 要设置的索引。  
  
 `value`  
 要设置的值。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 需要活动脚本上下文。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)