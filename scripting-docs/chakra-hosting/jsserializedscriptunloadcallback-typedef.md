---
title: "JsSerializedScriptUnloadCallback typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8d18c392-cca0-411e-9f2b-0d788b16161a
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsSerializedScriptUnloadCallback typedef
在运行时用完与脚本执行相关的所有资源后，由运行时调用。 此时，调用方应释放源（如果已加载）、字节代码和上下文。  
  
## 语法  
  
```  
 typedef void (CALLBACK * JsSerializedScriptUnloadCallback)(  
  _In_ JsSourceContext sourceContext  
);  
```  
  
#### 参数  
 `sourceContext`  
 传递到 `JsParseSerializedScriptWithCallback` 或 `JsRunSerializedScriptWithCallback` 的上下文。  
  
## 备注  
  
> [!WARNING]
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)