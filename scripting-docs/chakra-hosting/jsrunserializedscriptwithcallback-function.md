---
title: "JsRunSerializedScriptWithCallback 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0608d778-f65b-4dc5-a745-364aac57ef59
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# JsRunSerializedScriptWithCallback 函数
运行序列化脚本。 仅在需要时才提供延迟加载脚本源代码的功能。  
  
## 语法  
  
```  
STDAPI_(JsErrorCode) JsRunSerializedScriptWithCallback(  
  _In_ JsSerializedScriptLoadSourceCallback scriptLoadCallback,  
  _In_ JsSerializedScriptUnloadCallback scriptUnloadCallback,  
  _In_ BYTE *buffer,  
  _In_ JsSourceContext sourceContext,  
  _In_z_ const wchar_t *sourceUrl,  
  _Out_opt_ JsValueRef *result  
);  
  
```  
  
#### 参数  
 `scriptLoadCallback`  
 在需要加载脚本的源代码时调用回调。  
  
 `scriptUnloadCallback`  
 当不再需要序列化脚本和源代码时调用回调。  
  
 `buffer`  
 序列化的脚本。  
  
 `sourceContext`  
 一个标识脚本的 Cookie，它可由可调试的脚本上下文使用。 此上下文会传入 scriptLoadCallback 和 scriptUnloadCallback。  
  
 `sourceUrl`  
 该脚本的来源位置。  
  
 `result`  
 运行该脚本的结果（如果有）。 此参数可以为 null。  
  
## 返回值  
 如果该操作成功，则为代码 `JsNoError`，否则为失败代码。  
  
## 备注  
  
> [!NOTE]
>  此 API 尚不可用于应用商店应用。  
  
 需要活动脚本上下文。  
  
 运行时会保持缓冲区，直到从缓冲区创建的任何函数的所有实例都进行了垃圾回收。  随后它会调用 scriptUnloadCallback 以通知调用方可安全地释放。  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)