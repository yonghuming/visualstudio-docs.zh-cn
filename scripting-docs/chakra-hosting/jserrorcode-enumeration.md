---
title: "JsErrorCode 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsErrorCode"
helpviewer_keywords: 
  - "JsErrorCode 枚举"
ms.assetid: 4902f3f3-47a5-4e74-9c29-f96eeecbcda9
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# JsErrorCode 枚举
从 Chakra 托管 API 返回了错误代码。  
  
## 语法  
  
```  
enum JsErrorCode : unsigned int;  
```  
  
## 成员  
  
### 值  
  
|名称|描述|  
|--------|--------|  
|`JsErrorAlreadyDebuggingContext`|无法将上下文置于调试状态，因为它已处于调试状态。|  
|`JsErrorAlreadyProfilingContext`|上下文无法启动分析，因为已经开始分析。|  
|`JsErrorArgumentNotObject`|调用处理对象值的托管 API 时提供了非对象值。|  
|`JsErrorBadSerializedScript`|使用了错误的序列化脚本，或者序列化脚本由不同版本的 Chakra 引擎序列化。|  
|`JsErrorCannotDisableExecution`|运行时不支持可靠的脚本中断。|  
|`JsErrorCannotSerializeDebugScript`|无法在调试上下文中序列化脚本。|  
|`JsErrorCategoryEngine`|与引擎自身中发生的错误相关的一类错误。|  
|`JsErrorCategoryFatal`|预示引擎故障的一类错误。|  
|`JsErrorCategoryScript`|与脚本中的错误相关的一类错误。|  
|`JsErrorCategoryUsage`|用 API 自身用法不正确相关的一类错误。|  
|`JsErrorFatal`|在引擎中发生了错误。|  
|`JsErrorHeapEnumInProgress`|当前正在脚本上下文中执行堆枚举。|  
|`JsErrorIdleNotEnabled`|当主机未启用空闲处理时发出的空闲通知。|  
|`JsErrorInDisabledState`|运行时处于禁用状态。|  
|`JsErrorInExceptionState`|引擎处于异常状态，在清除异常之前，无法调用任何 API。|  
|`JsErrorInObjectBeforeCollectCallback`|集合回调前，不支持在对象中执行该操作。<br /><br /> 此枚举值仅在边缘模式下受到支持。|  
|`JsErrorInProfileCallback`|脚本上下文正处于配置文件回调过程中。|  
|`JsErrorInThreadServiceCallback`|当前正在执行线程服务回调。|  
|`JsErrorInvalidArgument`|托管 API 的参数无效。|  
|`JsErrorNoCurrentContext`|托管 API 要求上下文处于最新状态，但是没有最新的上下文。|  
|`JsErrorNotImplemented`|托管 API 尚未实现。|  
|`JsErrorNullArgument`|托管 API 的参数在上下文中为空，但该上下文不允许存在空值。|  
|`JsErrorObjectNotInspectable`|对象不能为解包到 `IInspectable` 指针。<br /><br /> 此枚举值仅在边缘模式下受到支持。|  
|`JsErrorOutOfMemory`|Chakra 引擎内存不足。|  
|`JsErrorPropertyNotSymbol`|一种托管 API，对符号属性 ID 起作用，但调用时使用非符号属性 ID。 如果使用非符号属性 ID 调用函数，`JsGetSymbolFromPropertyId` 将返回错误代码。<br /><br /> 此枚举值仅在边缘模式下受到支持。|  
|`JsErrorPropertyNotString`|一种托管 API，对字符串属性 ID 起作用，但调用时使用非字符串属性 ID。 如果使用非字符串属性 ID 调用函数，`JsGetPropertyNamefromId` 将返回错误代码。<br /><br /> 此枚举值仅在边缘模式下受到支持。|  
|`JsErrorRuntimeInUse`|不能释放仍在使用的运行时。|  
|`JsErrorScriptCompile`|JavaScript 编译失败。|  
|`JsErrorScriptEvalDisabled`|脚本已终止，因为它尝试使用 `eval` 或 `function` 而 eval 处于禁用状态。|  
|`JsErrorScriptException`|运行脚本时发生了 JavaScript 异常。|  
|`JsErrorScriptTerminated`|脚本因挂起运行时的请求而终止。|  
|`JsErrorWrongRuntime`|调用托管 API 时在不同的 JavaScript 运行时上创建对象。|  
|`JsErrorWrongThread`|调用托管 API 的线程有误。|  
|`JsNoError`|成功时的错误代码。|  
  
## 要求  
 **标头：**jsrt.h  
  
## 请参阅  
 [参考（JavaScript 运行时）](../chakra-hosting/reference-javascript-runtime.md)