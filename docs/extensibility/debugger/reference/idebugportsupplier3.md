---
title: "IDebugPortSupplier3 | Microsoft Docs"
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
  - "IDebugPortSupplier3"
helpviewer_keywords: 
  - "IDebugPortSupplier3 接口"
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplier3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口允许调用方确定端口提供程序是否可以保留端口 \(通过编写自己写入磁盘\) 在调试器中调用然后获取这些之间的列表保留的端口。  
  
## 语法  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## 实现者说明  
 自定义端口提供程序实现此接口支持持久化或保存的端口信息到磁盘。  在对象必须实现此接口和 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) 接口相同。  
  
## 调用方的说明  
 调用 `IDebugPortSupplier2` 接口的 [QueryInterface](/visual-cpp/atl/queryinterface) 获取此接口。  
  
## 方法按 Vtable 顺序  
 除了从 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) 接口继承的方法之外，此接口支持下列:  
  
|方法|说明|  
|--------|--------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|返回端口提供程序是否可以保留端口 \(通过编写自己写入磁盘\) 在调试器中调用之间。|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|返回可用于通过任何端口枚举向磁盘写入由此端口提供程序的对象。|  
  
## 备注  
 如果端口提供程序可以保留在调用中的端口，它应实现此接口。  填充端口，该端口提供程序向磁盘时实例化，并编写的，当销毁时端口提供程序。  
  
 调试引擎与端口提供程序通常不进行交互，并不需要此接口。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)