---
title: "JsRuntimeAttributes 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsRuntimeAttributes"
helpviewer_keywords: 
  - "JsRuntimeAttributes 枚举"
ms.assetid: f76d82e9-a695-4d6a-96c1-b3a4d27fed68
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# JsRuntimeAttributes 枚举
运行时的特性。  
  
## 语法  
  
```  
enum JsRuntimeAttributes;  
```  
  
## 成员  
  
### 值  
  
|名称|说明|  
|--------|--------|  
|`JsRuntimeAttributeAllowScriptInterrupt`|运行时应支持可靠的脚本中断。 这将以少量运行时性能代价增加运行时检查脚本中断请求的位置数量。|  
|`JsRuntimeAttributeDisableBackgroundWork`|运行时将不在后台线程中执行任何作业（例如垃圾回收）。|  
|`JsRuntimeAttributeDisableEval`|使用 `eval` 或 `function` 构造函数将引发异常。|  
|`JsRuntimeAttributeDisableNativeCodeGeneration`|运行时将不会生成本机代码。|  
|`JsRuntimeAttributeEnableExperimentalFeatures`|运行时将启用所有实验性功能。|  
|`JsRuntimeAttributeEnableIdleProcessing`|主机将调用 `JsIdle`，以启用空闲处理。 否则，运行时在管理内存方面会略微主动一些。|  
|`JsRuntimeAttributeDispatchSetExceptionsToDebugger`|调用 `JsSetException` 也会将异常分派给脚本调试器（如有），从而让调试器有机会在异常上中断。|  
|`JsRuntimeAttributeNone`|没有特殊特性。|  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)