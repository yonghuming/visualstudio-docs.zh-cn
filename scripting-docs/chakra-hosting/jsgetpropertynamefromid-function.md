---
title: "JsGetPropertyNameFromId 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetPropertyNameFromId"
helpviewer_keywords: 
  - "JsGetPropertyNameFromId 函数"
ms.assetid: b4ca442c-573d-4bc3-adf7-1b8d48480b3a
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsGetPropertyNameFromId 函数
获取与属性 ID 关联的名称。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsGetPropertyNameFromId(  
   _In_ JsPropertyIdRef propertyId,  
   _Outptr_result_z_ const wchar_t **name  
);  
```  
  
#### 参数  
 `propertyId`  
 要获取其名称的属性 ID.  
  
 `name`  
 与属性 ID 关联的名称。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 需要活动脚本上下文。  
  
 只要运行时处于活动状态且在释放运行时后不能被使用，返回的缓冲区均有效。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)