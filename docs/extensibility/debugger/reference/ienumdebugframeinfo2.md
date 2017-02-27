---
title: "IEnumDebugFrameInfo2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugFrameInfo2"
helpviewer_keywords: 
  - "IEnumDebugFrameInfo2"
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugFrameInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口枚举 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 结构。  
  
## 语法  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎 \(DE\)实现此接口提供描述当前调用堆栈框架的列表。  
  
## 调用方的说明  
 Visual Studio 会调用 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 获取此接口，只要断点、异常或暂停正在调试的程序发生。  
  
## 方法按 Vtable 顺序  
 下表显示 `IEnumDebugFrameInfo2`方法。  
  
|方法|说明|  
|--------|--------|  
|[下一步](../Topic/IEnumDebugFrameInfo2::Next.md)|检索 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 结构指定数目的枚举序列的。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|跳过 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 结构指定数目的枚举序列的。|  
|[重置](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|重置枚举序列与开头。|  
|[克隆](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|创建包含枚举状态和枚举当前枚举数相同的枚举数。|  
|[GetCount](../Topic/IEnumDebugFrameInfo2::GetCount.md)|获取 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 结构数在枚举数。|  
  
## 备注  
 Visual Studio 获取此接口，第一步处理断点、异常或用户生成的暂停正在调试的程序。  [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 结构中表示当前调用堆栈，该函数请在列表中开始时调用，并最旧的函数调用在列表末尾。  每 `FRAMEINFO` 表示堆栈帧，可以在其中计算表达式，并且局部变量查看的上下文。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)