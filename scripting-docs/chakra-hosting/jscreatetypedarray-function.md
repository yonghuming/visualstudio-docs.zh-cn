---
title: "JsCreateTypedArray 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 937a2a91-6f5f-4aaa-a018-d3089702bf36
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsCreateTypedArray 函数
创建 JavaScript 类型的数组对象。  
  
## 语法  
  
```cpp  
STDAPI_(JsErrorCode) JsCreateTypedArray(  
   _In_ JsTypedArrayType arrayType,  
   _In_ JsValueRef baseArray,  
   _In_ unsigned int byteOffset,  
   _In_ unsigned int elementLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### 参数  
 `arrayType`  
 要创建的数组类型。  
  
 `baseArray`  
 新数组的基数组。  如果没有基数组，请使用 `JS_INVALID_REFERENCE`。  
  
 `byteOffset`  
 自 `baseArray` \(`ArrayBuffer`\) 开始，供结果类型化数组引用的偏移量（以字节为单位）。  仅当 `baseArray` 是 `ArrayBuffer` 对象时才适用。  否则，必须为 0。  
  
 `elementLength`  
 数组中的元素数。  仅当出现以下条件时才适用：无需 `baseArray`（`baseArray` 是 `JS_INVALID_REFERENCE`）创建新类型化数组时，或 `baseArray` 是 `ArrayBuffer` 对象时。  否则，必须为 0。  
  
 `result`  
 新类型化数组对象。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 `baseArray` 可以是 `ArrayBuffer`、另一个类型化数组或 JavaScript `Array`。  如果返回的类型化的数组为`ArrayBuffer`，则它将使用 `baseArray`，否则，将创建和使用基础源数组的副本。  
  
 需要活动脚本上下文。  
  
 此 API 仅在“边缘”模式下受到支持。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)