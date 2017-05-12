---
title: "JsCreateExternalArrayBuffer 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a02aaec-0f67-4bf9-b37c-71cdb1410ca4
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsCreateExternalArrayBuffer 函数
创建 Javascript `ArrayBuffer` 对象以访问外部内存。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsCreateExternalArrayBuffer(  
  _Pre_maybenull_ _Pre_writable_byte_size_(byteLength) void *data,  
  _In_ unsigned int byteLength,  
  _In_opt_ JsFinalizeCallback finalizeCallback,  
  _In_opt_ void *callbackState,  
  _Out_ JsValueRef *result  
);  
  
```  
  
#### 参数  
 `data`  
 指向外部内存的指针。  
  
 `byteLength`  
 外部内存中的字节数。  
  
 `finalizeCallback`  
 完成对象时的回调。 可能为 null。  
  
 `callbackState`  
 将传回到 finalizeCallback 的用户提供的状态。  
  
 `result`  
 新的 `ArrayBuffer` 对象。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 需要活动脚本上下文。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)