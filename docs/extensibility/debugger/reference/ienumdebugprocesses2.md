---
title: "IEnumDebugProcesses2 | Microsoft Docs"
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
  - "IEnumDebugProcesses2"
helpviewer_keywords: 
  - "IEnumDebugProcesses2"
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugProcesses2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口、枚举过程运行在调试端口。  
  
## 语法  
  
```  
IEnumDebugProcesses : IUnknown  
```  
  
## 实现者说明  
 自定义端口提供程序实现此接口提供进程列表运行在端口。  
  
## 调用方的说明  
 Visual Studio 会调用 [EnumProcesses](../Topic/IDebugPort2::EnumProcesses.md) 获取此接口。  
  
## 方法按 Vtable 顺序  
 下表显示 `IEnumDebugProcesses2`方法。  
  
|方法|说明|  
|--------|--------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|在枚举顺序检索一个指定的数量。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|在枚举序列跳过一个指定的数量。|  
|[重置](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|重置枚举序列与开头。|  
|[克隆](../Topic/IEnumDebugProcesses2::Clone.md)|创建包含枚举状态和枚举当前枚举数相同的枚举数。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|在枚举器获取数量。|  
  
## 备注  
 Visual Studio 使用此接口填充 **处理** 窗口。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumProcesses](../Topic/IDebugPort2::EnumProcesses.md)