---
title: "JsGetPropertyIdFromName 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetPropertyIdFromName"
helpviewer_keywords: 
  - "JsGetPropertyIdFromName 函数"
ms.assetid: 1674906f-746a-4c62-99cd-023276683a86
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsGetPropertyIdFromName 函数
获取与名称关联的属性 ID。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsGetPropertyIdFromName(  
   _In_z_ const wchar_t *name,  
   _Out_ JsPropertyIdRef *propertyId  
);  
```  
  
#### 参数  
 `name`  
 要获取或创建的属性 ID 的名称。  名称可能仅由数字组成。  
  
 `propertyId`  
 在此运行时中给定名称的属性 ID。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 属性 ID 特定于某个上下文但不能跨上下文使用。  
  
 需要活动脚本上下文。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)