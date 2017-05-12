---
title: "IDebugStackFrame 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugStackFrame 接口"
ms.assetid: e95c1b4f-17c1-490c-a56b-c25fa45d4822
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame 接口
表示在线程堆栈的逻辑堆栈帧。  调用 `IDebugStackFrame::QueryInterface` 方法获取 `IDebugExpressionContext` 接口，允许表达式计算和"监视"窗口。  
  
 除了从 `IUnknown` 继承的方法之外，`IDebugStackFrame` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IDebugStackFrame::GetCodeContext](../../winscript/reference/idebugstackframe-getcodecontext.md)|返回当前代码上下文与堆栈帧。|  
|[IDebugStackFrame::GetDescriptionString](../../winscript/reference/idebugstackframe-getdescriptionstring.md)|返回堆栈帧的简短或长的文本说明。|  
|[IDebugStackFrame::GetLanguageString](../../winscript/reference/idebugstackframe-getlanguagestring.md)|返回该语言的简短或长的文本说明。|  
|[IDebugStackFrame::GetThread](../../winscript/reference/idebugstackframe-getthread.md)|返回线程与此堆栈帧。|  
|[IDebugStackFrame::GetDebugProperty](../../winscript/reference/idebugstackframe-getdebugproperty.md)|返回当前帧的属性浏览器。|