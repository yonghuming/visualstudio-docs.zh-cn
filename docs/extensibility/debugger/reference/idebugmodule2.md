---
title: "IDebugModule2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule2"
helpviewer_keywords: 
  - "IDebugModule2 接口"
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugModule2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示模块是，可执行单元程序 \(如 DLL。  
  
## 语法  
  
```  
IDebugModule2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎 \(DE\)实现此接口表示模块和提供对有关该模块的信息。  
  
## 调用方的说明  
 为 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) 的调用返回此接口。  DE 发送 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) 接口添加到该会话调试使用 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 方法管理器 \(SDM\)的。  
  
 此接口。还可以返回到 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)的调用返回\) 的 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 结构 \(。  
  
 [下一步](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) 还返回此接口 \([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) 返回 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) 接口\)。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugModule2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|获取描述此模块的 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) 。|  
|[ReloadSymbols\_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|过时。  不要使用。  重新加载此模块的符号。|  
  
## 备注  
 模块信息在 IDE 中 **模块** 窗口中显示。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)