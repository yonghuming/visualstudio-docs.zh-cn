---
title: "IEnumDebugPorts2 | Microsoft Docs"
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
  - "IEnumDebugPorts2"
helpviewer_keywords: 
  - "IEnumDebugPorts2"
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugPorts2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口枚举计算机或端口提供程序的端口。  
  
## 语法  
  
```  
IEnumDebugPorts2 : IUnknown  
```  
  
## 实现者说明  
 自定义端口提供程序实现此接口表示该提供程序创建的端口列表。  Visual Studio 实现此接口支持其自身的端口提供程序。  
  
## 调用方的说明  
 调用 [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) 获取表示端口的列表此接口可创建由端口提供程序。  调用 [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) 获取表示已保存到磁盘端口的列表此接口。  
  
## 方法按 Vtable 顺序  
 下表显示 `IEnumDebugPorts2`方法。  
  
|方法|说明|  
|--------|--------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|检索端口指定数目的枚举序列的。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|跳过端口指定数目的枚举序列的。|  
|[重置](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|重置枚举序列与开头。|  
|[克隆](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|创建包含枚举状态和枚举当前枚举数相同的枚举数。|  
|[GetCount](../Topic/IEnumDebugPorts2::GetCount.md)|获取端口数枚举数。|  
  
## 备注  
 Visual Studio 使用此接口来帮助填充为附加使用的端口进程列表。  
  
 调试引擎通常不使用此接口。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)