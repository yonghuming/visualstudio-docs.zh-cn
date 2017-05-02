---
title: "JsSetIndexedPropertiesToExternalData 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: cee2d86d-ed42-4acb-86ef-95a67e63d0d6
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsSetIndexedPropertiesToExternalData 函数
将对象的索引属性设置为外部数据。  外部数据将用作对象索引属性的后备存储，并像类型化数组一样进行访问。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsSetIndexedPropertiesToExternalData(  
   _In_ JsValueRef object,  
   _In_ void* data,  
   _In_ JsTypedArrayType arrayType,  
   _In_ unsigned int elementLength  
);  
```  
  
#### 参数  
 `object`  
 要对其执行操作的对象。  
  
 `data`  
 要用作对象索引属性的后备存储的外部数据。  
  
 `arrayType`  
 外部数据中的数组元素类型。  
  
 `elementLength`  
 外部数据中数组元素的数目。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 需要活动脚本上下文。  
  
 此 API 仅在“边缘”模式下受到支持。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)