---
title: "JsMemoryEventType 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsMemoryEventType"
helpviewer_keywords: 
  - "JsMemoryEventType 枚举"
ms.assetid: b4b176b6-b536-472e-8999-95b681a1df55
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsMemoryEventType 枚举
分配回调事件类型。  
  
## 语法  
  
```  
enum JsMemoryEventType;  
```  
  
## 成员  
  
### 值  
  
|名称|描述|  
|--------|--------|  
|`JsMemoryAllocate`|指示内存分配请求。|  
|`JsMemoryFailure`|指示失败的分配事件。|  
|`JsMemoryFree`|指示内存释放事件。|  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)