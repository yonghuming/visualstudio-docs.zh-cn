---
title: "JsCreateExternalObject 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsCreateExternalObject"
helpviewer_keywords: 
  - "JsCreateExternalObject 函数"
ms.assetid: 6bcef506-93fb-429b-b06a-a971ff0b71f3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsCreateExternalObject 函数
创建存储某些外部数据的新对象。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsCreateExternalObject(  
   _In_opt_ void *data,  
   _In_opt_ JsFinalizeCallback finalizeCallback,  
   _Out_ JsValueRef *object  
);  
```  
  
#### 参数  
 `data`  
 对象将表示的外部数据。  可能为 null。  
  
 `finalizeCallback`  
 完成对象时的回调。  可能为 null。  
  
 `object`  
 新对象。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 需要活动脚本上下文。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)