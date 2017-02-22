---
title: "IEnumDebugModules2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugModules2"
helpviewer_keywords: 
  - "IEnumDebugModules2"
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugModules2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口的模块列表。  
  
## 语法  
  
```  
IEnumDebugModules2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎 \(DE\)实现此接口表示为程序加载的模块列表。  
  
## 调用方的说明  
 Visual Studio 会调用 [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) 获取此接口。  
  
## 方法按 Vtable 顺序  
 下表显示 `IEnumDebugModules2`方法。  
  
|方法|说明|  
|--------|--------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|检索模块指定数目的枚举序列的。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|跳过模块指定数目的枚举序列的。|  
|[重置](../Topic/IEnumDebugModules2::Reset.md)|重置枚举序列与开头。|  
|[克隆](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|创建包含枚举状态和枚举当前枚举数相同的枚举数。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|获取模块数量。|  
  
## 备注  
 Visual Studio 主使用此接口更新 **模块** 窗口。  
  
 为调试在 Visual Studio 中，程序是的代码命令逻辑顺序可能跨模块边界，因此需要模块列表一个 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 接口的。  列表中的第一个模块通常包含初始对关联的程序入口点。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)