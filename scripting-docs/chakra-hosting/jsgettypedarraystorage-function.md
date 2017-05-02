---
title: "JsGetTypedArrayStorage 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 52e4ac5f-cc71-456d-95de-a48f7327503d
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsGetTypedArrayStorage 函数
获取由类型化数组使用的基础内存存储。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsGetTypedArrayStorage(  
   _In_ JsValueRef typedArray,  
   _Outptr_result_bytebuffer_(*bufferLength) BYTE **buffer,  
   _Out_ unsigned int *bufferLength,  
   _Out_opt_ JsTypedArrayType *arrayType,  
   _Out_opt_ int *elementSize  
);  
```  
  
#### 参数  
 `typedArray`  
 类型化数组实例。  
  
 `buffer`  
 数组的缓冲区。  返回的缓冲区的生存期与数组的生存期相同。  缓冲区指针不能算作对用于垃圾回收的数组的引用。  
  
 `bufferLength`  
 缓冲区中的字节数。  
  
 `arrayType`  
 数组的类型。  
  
 `elementSize`  
 数组的元素的大小。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 需要活动脚本上下文。  
  
 此 API 仅在“边缘”模式下受到支持。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)