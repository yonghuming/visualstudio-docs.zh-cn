---
title: "IDebugSymbolSearchEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolSearchEvent2"
helpviewer_keywords: 
  - "IDebugSymbolSearchEvent2"
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugSymbolSearchEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

调试引擎 \(DE\)发送此接口指示正在调试的模块的调试符号加载的。  
  
## 语法  
  
```  
IDebugSymbolSearchEvent2 : IUnknown  
```  
  
## 实现者说明  
 DE implements 报告此接口的模块的符号加载的。  在对象必须实现 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 接口和此接口相同。  SDM 使用 [QueryInterface](/visual-cpp/atl/queryinterface) 访问 `IDebugEvent2` 接口。  
  
## 调用方的说明  
 DE 创建和发送此事件对象报告模块的符号加载的。  事件发送通过使用 SDM 提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回调函数，则附加到正在调试的程序。  
  
## 方法按 Vtable 顺序  
 `IDebugSymbolSearchEvent2` 接口公开下列方法。  
  
|方法|说明|  
|--------|--------|  
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|检索有关符号搜索结果的信息。|  
  
## 备注  
 将发送此事件，即使符号未能加载。  调用 `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` 允许此事件的处理程序确定模块是否确实存在任何符号。  
  
 Visual Studio 通常使用此事件更新加载符号的状态。 **模块** 窗口中。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)