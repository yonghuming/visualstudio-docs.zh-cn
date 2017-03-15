---
title: "IDebugAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAddress"
helpviewer_keywords: 
  - "IDebugAddress 接口"
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示项目的地址。  它由符号处理程序返回。  
  
## 语法  
  
```  
IDebugAddress : IUnknown  
```  
  
## 实现者说明  
 符号提供程序实现此接口表示对象的地址。  
  
## 调用方的说明  
 在大多数接口中的许多方法返回此接口。  
  
## 方法按 Vtable 顺序  
 此接口执行以下方法:  
  
|方法|说明|  
|--------|--------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|检索描述对象及其位置的 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 结构。|  
  
## 备注  
 符号提供程序返回此接口表示对象及其位置在特定范围内 \(例如，函数、方法或类\)。  此接口返回自并传递给符号提供程序和表达式计算器的各种方法。  通常，符号提供程序需要解释此接口内容的唯一实体。  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [符号提供程序接口](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)