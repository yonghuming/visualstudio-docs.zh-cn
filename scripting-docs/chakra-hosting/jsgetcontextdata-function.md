---
title: "JsGetContextData 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f5d7e446-267a-4a80-a427-6e1b95a3391b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# JsGetContextData 函数
获取 JsrtContext 上设置的内部数据。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsGetContextData(  
  _In_ JsContextRef context,  
  _Out_ void **data  
);  
```  
  
#### 参数  
 `context`  
 要从中获取数据的上下文。  
  
 `data`  
 指向数据将返回到的数据的指针。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 需要活动脚本上下文。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)