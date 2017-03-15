---
title: "IDebugBeforeSymbolSearchEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugBeforeSymbolSearchEvent2 接口"
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugBeforeSymbolSearchEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

在符号加载过程中，调试引擎 \(DE\)发送此接口添加到该会话调试经理 \(SDM\)设置状态栏消息。  
  
## 语法  
  
```  
IDebugBeforeSymbolSearchEvent2 : IUnknown  
```  
  
## 实现者说明  
 DE 此接口的 implements，则它必须将状态栏消息在加载符号过程。  此接口只实现由调试工作与的引擎或这些脚本解释器的部件。  在对象必须实现 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 接口和此接口相同 \(SDM 使用 **QI** 访问 **IDebugEvent2** 接口\)。  
  
## 调用方的说明  
 在符号加载过程中，选中状态，那么，当它必须将状态栏消息、创建和发送此事件对象。  ，它附加到正在调试的程序，该事件发送通过使用 SDM 提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回调函数。  
  
## 方法  
 下表显示 `IDebugBeforeSymbolSearchEvent2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|检索当前正在调试的模块的名称。|  
  
## 要求  
 标题:Msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll