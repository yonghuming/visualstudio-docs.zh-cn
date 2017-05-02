---
title: "活动脚本调试器常量、枚举和结构 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "活动脚本调试器常量"
  - "活动脚本调试器枚举"
  - "活动脚本调试器结构"
ms.assetid: b80b9207-fb19-4ee2-85fb-41f8c26e7706
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 活动脚本调试器常量、枚举和结构
下面的常量、枚举和结构由 Active Debugging 接口使用。  
  
## 常量、枚举和结构  
  
|常量|说明|  
|--------|--------|  
|[APPBREAKFLAGS 常量](../../winscript/reference/appbreakflags-enumeration.md)|指示当前的应用程序和线程调试状态。|  
|[DEBUG\_TEXT 常量](../../winscript/reference/debug-text-constants.md)|[IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md) 期间使用的选项标志。|  
|[TEXT\_DOC\_ATTR 常量](../../winscript/reference/text-doc-attr-constants.md)|描述文档的特性。|  
  
|枚举|说明|  
|--------|--------|  
|[APPBREAKFLAGS 常量](../../winscript/reference/appbreakflags-enumeration.md)|指示当前的应用程序和线程调试状态。|  
|[APPLICATION\_NODE\_EVENT\_FILTER 枚举](../../winscript/reference/application-node-event-filter-enumeration.md)|指示要使用筛选器排除的节点。|  
|[BREAKPOINT\_STATE 枚举](../../winscript/reference/breakpoint-state-enumeration.md)|指示断点的状态。|  
|[BREAKREASON 枚举](../../winscript/reference/breakreason-enumeration.md)|指示造成中断的原因。|  
|[BREAKRESUMEACTION 枚举](../../winscript/reference/breakresumeaction-enumeration.md)|描述如何从断点继续。|  
|[DOCUMENTNAMETYPE 枚举](../../winscript/reference/documentnametype-enumeration.md)|描述为文档获取哪种类型。|  
|[ERRORRESUMEACTION 枚举](../../winscript/reference/errorresumeaction-enumeration.md)|描述如何从运行时错误继续。|  
|[JS\_PROPERTY\_ATTRIBUTES 枚举](../../winscript/reference/js-property-attributes-enumeration.md)|指示属性的特性。|  
|[JS\_PROPERTY\_MEMBERS 枚举](../../winscript/reference/js-property-members-enumeration.md)|在对象成员的请求中用于指定信息类型返回的标志。|  
|[JsDebugReadMemoryFlags 枚举](../../winscript/reference/jsdebugreadmemoryflags-enumeration.md)|读取内存时用于指定行为的标志。|  
|[SCRIPT\_DEBUGGER\_OPTIONS 枚举](../../winscript/reference/script-debugger-options-enumeration.md)|指示应用于附加调试器的选项或功能集。|  
|[SCRIPT\_ERROR\_DEBUG\_EXCEPTION\_THROWN\_KIND 枚举](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md)|指示已引发异常的类型。|  
|[SOURCE\_TEXT\_ATTR 常量](../../winscript/reference/source-text-attr-enumeration.md)|描述单个源文本字符的特性。|  
  
|结构|说明|  
|--------|--------|  
|[DebugStackFrameDescriptor 结构](../../winscript/reference/debugstackframedescriptor-structure.md)|枚举堆栈帧并在同一线程上将多个枚举器的输出合并。|  
|[JS\_NATIVE\_FRAME 结构](../../winscript/reference/js-native-frame-structure.md)|表示堆栈帧。|  
|[JsDebugPropertyInfo 结构](../../winscript/reference/jsdebugpropertyinfo-structure.md)|指示与某一属性有关的信息。|  
|[TEXT\_DOCUMENT\_ARRAY 结构](../../winscript/reference/text-document-array-structure.md)|提供一组文档。|