---
title: "JsObjectBeforeCollectCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: f21a064a-579f-44cb-9d21-76b62e8c18f5
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsObjectBeforeCollectCallback Typedef
在收集对象前调用的回调。  
  
## 语法  
  
```  
typedef void (CALLBACK *JsObjectBeforeCollectCallback)(  
  _In_ JsRef ref,  
  _In_opt_ void *callbackState  
);  
```  
  
#### 参数  
 `ref`  
 要收集的对象。  
  
 `callbackState`  
 传递到 `JsSetObjectBeforeCollectCallback` 的状态。  
  
## 备注  
 此 API 仅在“边缘”模式下受到支持。  
  
## 要求  
 jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)