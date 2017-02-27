---
title: "IEnumDebugAddresses | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugAddresses"
helpviewer_keywords: 
  - "IEnumDebugAddresses 接口"
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IEnumDebugAddresses
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示实现 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 接口的对象的集合。  
  
## 语法  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## 实现者说明  
 此接口由符号提供程序实现提供了一组对象实现 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 接口。  注意不是标准 COM 枚举由于 [GetCount](../Topic/IEnumDebugAddresses::GetCount.md) 方法的显示。  
  
## 调用方的说明  
 此接口由 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) 和 [GetAddressesFromPosition](../Topic/IDebugSymbolProvider::GetAddressesFromPosition.md)返回。  
  
## 方法按 Vtable 顺序  
 此接口执行以下操作方法。  
  
|方法|说明|  
|--------|--------|  
|[下一步](../Topic/IEnumDebugAddresses::Next.md)|枚举检索下一组 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 对象。|  
|[Skip](../Topic/IEnumDebugAddresses::Skip.md)|跳过项指定数目的。|  
|[重置](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|重置枚举先 enter。|  
|[克隆](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|检索当前枚举的副本。|  
|[GetCount](../Topic/IEnumDebugAddresses::GetCount.md)|检索项数在枚举的。|  
  
## 备注  
 调试引擎通常用于此接口来帮助确定适当的地址生成一个表达式计算器。  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [符号提供程序接口](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../Topic/IDebugSymbolProvider::GetAddressesFromPosition.md)