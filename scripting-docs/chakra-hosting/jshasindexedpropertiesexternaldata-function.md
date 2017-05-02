---
title: "JsHasIndexedPropertiesExternalData 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: c676db20-3ef1-4f84-8b26-3e06fe0ab2bf
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsHasIndexedPropertiesExternalData 函数
确定对象在外部数据中是否具有其索引属性。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsHasIndexedPropertiesExternalData(  
   _In_ JsValueRef object,  
   _Out_ bool* value  
);  
```  
  
#### 参数  
 `object`  
 对象。  
  
 `value`  
 对象在外部数据中是否具有其索引属性。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
 此 API 仅在“边缘”模式下受到支持。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)