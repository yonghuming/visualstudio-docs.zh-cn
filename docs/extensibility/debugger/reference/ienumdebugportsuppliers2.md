---
title: "IEnumDebugPortSuppliers2 | Microsoft Docs"
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
  - "IEnumDebugPortSuppliers2"
helpviewer_keywords: 
  - "IEnumDebugPortSuppliers2"
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugPortSuppliers2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口枚举端口提供程序。  
  
## 语法  
  
```  
IEnumDebugPortSuppliers2 : IUnknown  
```  
  
## 实现者说明  
 Visual Studio 实现此接口表示端口提供程序列表。  
  
## 调用方的说明  
 调用 [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) 获取端口提供程序列表。  
  
## 方法按 Vtable 顺序  
 下表显示 `IEnumDebugPortSuppliers2`方法。  
  
|方法|说明|  
|--------|--------|  
|[下一步](../Topic/IEnumDebugPortSuppliers2::Next.md)|检索端口提供程序指定数目的枚举序列的。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|跳过端口提供程序指定数目的枚举序列的。|  
|[重置](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|重置枚举序列与开头。|  
|[克隆](../Topic/IEnumDebugPortSuppliers2::Clone.md)|创建包含枚举状态和枚举当前枚举数相同的枚举数。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|获取端口提供程序的数量枚举数。|  
  
## 备注  
 调试引擎通常不需要获取此接口。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)