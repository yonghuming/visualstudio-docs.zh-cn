---
title: "JsGetArrayBufferStorage 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 712ae298-36a9-47ef-b089-e51835c056bc
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsGetArrayBufferStorage 函数
获取由 `ArrayBuffer` 使用的基础内存存储。  
  
## 语法  
  
```  
JsErrorCode STDAPI_ JsGetArrayBufferStorage(  
   _In_ JsValueRef arrayBuffer,  
   _Outptr_result_bytebuffer_(*bufferLength) BYTE **buffer,  
   _Out_ unsigned int *bufferLength  
);  
```  
  
#### 参数  
 `arrayBuffer`  
 ArrayBuffer 实例。  
  
 `buffer`  
 ArrayBuffer 缓冲区。  所返回缓冲区的生存期与 `ArrayBuffer` 的生存期相同。  缓冲区指针不能算作对用于垃圾回收的 `ArrayBuffer` 数组的引用。  
  
 `bufferLength`  
 缓冲区中的字节数。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 需要活动脚本上下文。  
  
 此 API 仅在“边缘”模式下受到支持。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)