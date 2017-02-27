---
title: "IDebugModule3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule3"
helpviewer_keywords: 
  - "IDebugModule3 接口"
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugModule3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示支持符号和 JustMyCode 状态的备用位置的模块。  
  
## 语法  
  
```  
IDebugModule3 : IDebugModule2  
```  
  
## 实现者说明  
 调试引擎 \(DE\)实现此接口支持符号的备用位置与 JustMyCode 状态使用 \(“JustMyCode”定义参见 [Visual Studio 调试器术语表](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) \)。  
  
## 调用方的说明  
 为 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) 的调用返回此接口。  DE 发送 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) 接口添加到该会话调试使用 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 方法管理器 \(SDM\)的。  此外，对于 [QueryInterface](/visual-cpp/atl/queryinterface) 的调用在 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) 接口返回此接口。  
  
## 方法按 Vtable 顺序  
 除了在 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) 接口的方法之外，此接口执行以下方法:  
  
|方法|说明|  
|--------|--------|  
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|返回符号和搜索每个路径的结果的搜索路径的列表。|  
|[LoadSymbols](../Topic/IDebugModule3::LoadSymbols.md)|加载并初始化当前模块的符号。|  
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|返回指定模块是否的标志表示用户代码。|  
|[SetJustMyCodeState](../Topic/IDebugModule3::SetJustMyCodeState.md)|指定是否应考虑模块用户代码。|  
  
## 备注  
 Visual Studio 是此接口典型的使用者。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)