---
title: "IEnumDebugPrograms2 | Microsoft Docs"
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
  - "IEnumDebugPrograms2"
helpviewer_keywords: 
  - "IEnumDebugPrograms2"
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugPrograms2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口枚举运行在当前程序的调试会话。  
  
## 语法  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎 \(DE\)实现此接口提供 DE 正在调试的程序的列表。  
  
## 调用方的说明  
 Visual Studio 会调用 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) 获取此接口。   Visual Studio 不使用[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) 。  
  
## 方法按 Vtable 顺序  
 下表显示 `IEnumDebugPrograms2`方法。  
  
|方法|说明|  
|--------|--------|  
|[下一步](../Topic/IEnumDebugPrograms2::Next.md)|检索程序指定数目的枚举序列的。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|跳过程序指定数目的枚举序列的。|  
|[重置](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|重置枚举序列与开头。|  
|[克隆](../Topic/IEnumDebugPrograms2::Clone.md)|创建包含枚举状态和枚举当前枚举数相同的枚举数。|  
|[GetCount](../Topic/IEnumDebugPrograms2::GetCount.md)|获取程序数在枚举数。|  
  
## 备注  
 Visual Studio 使用此接口:  
  
-   填充 **模块** 窗口 \(通过调用 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) 然后对每个程序的 [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) \)。  
  
-   填充 **附加的进程** 列表 \(通过调用 `IDebugProcess2::EnumPrograms` 然后对每个 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 接口的 [QueryInterface](/visual-cpp/atl/queryinterface) 获取 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) 接口\)。  
  
-   生成可以调试进程中的每个程序 DES 的列表 \(使用 [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)\)。  
  
-   应用编辑并继续 " \(ENC\) 更新为每个程序 \(通过调用 IDebugProcess2:: EnumPrograms 然后调用 [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)\)。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)