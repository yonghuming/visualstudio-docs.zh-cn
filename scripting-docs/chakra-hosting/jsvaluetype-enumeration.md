---
title: "JsValueType 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsValueType"
helpviewer_keywords: 
  - "JsValueType 枚举"
ms.assetid: 6645e723-e554-41fc-b622-ab54ee044b3d
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# JsValueType 枚举
JsValueRef 的 JavaScript 类型。  
  
## 语法  
  
```  
enum JsValueType {  
    JsUndefined      = 0,  
    JsNull           = 1,  
    JsNumber         = 2,  
    JsString         = 3,  
    JsBoolean        = 4,  
    JsObject         = 5,  
    JsFunction       = 6,  
    JsError          = 7,  
    JsArray          = 8,  
    JsSymbol         = 9,  
    JsArrayBuffer    = 10,  
    JsTypedArray     = 11,  
    JsDataView       = 12,  
};  
```  
  
## 成员  
  
### 值  
  
|名称|描述|  
|--------|--------|  
|`JsUndefined`|值为 `undefined` 值。|  
|`JsNull`|值为 `null` 值。|  
|`JsNumber`|值为 JavaScript 数值。|  
|`JsString`|值为 JavaScript 字符串值。|  
|`JsBoolean`|值为 JavaScript 布尔值。|  
|`JsObject`|值为 JavaScript 对象值。|  
|`JsFunction`|值为 JavaScript 函数对象值。|  
|`JsError`|值为 JavaScript 错误对象值。|  
|`JsArray`|值为 JavaScript 数组对象值。|  
|`JsSymbol`|值为 JavaScript 符号值。<br /><br /> 此枚举值仅在边缘模式下受到支持。|  
|`JsArrayBuffer`|值为 JavaScript `ArrayBuffer` 对象值。<br /><br /> 此枚举值仅在边缘模式下受到支持。|  
|`JsTypedArray`|值为 JavaScript 类型的数组对象值。<br /><br /> 此枚举值仅在边缘模式下受到支持。|  
|`JsDataView`|值为 JavaScript `DataView` 对象值。<br /><br /> 此枚举值仅在边缘模式下受到支持。|  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)