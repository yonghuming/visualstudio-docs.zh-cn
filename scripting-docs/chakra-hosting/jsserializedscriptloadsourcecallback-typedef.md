---
title: "JsSerializedScriptLoadSourceCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9406c488-76ac-49e5-b305-39751f3412ea
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsSerializedScriptLoadSourceCallback Typedef
由运行时调用，用于加载序列化脚本的源代码。 在 `JsSerializedScriptUnloadCallback` 之前，调用方必须使脚本缓冲区保持有效。  
  
## 语法  
  
```  
typedef bool (CALLBACK * JsSerializedScriptLoadSourceCallback)(  
  _In_ JsSourceContextsourceContext,  
  _Outptr_result_z_ const wchar_t** scriptBuffer  
);  
```  
  
#### 参数  
 `sourceContext`  
 传递到 `JsParseSerializedScriptWithCallback` 或 `JsRunSerializedScriptWithCallback` 的上下文。  
  
 `scriptBuffer`  
 返回的脚本。  
  
## 备注  
  
> [!WARNING]
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)