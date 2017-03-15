---
title: "IDebugDynamicField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDynamicField"
helpviewer_keywords: 
  - "IDebugDynamicField 接口"
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugDynamicField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示变量的类型。  
  
## 语法  
  
```  
IDebugDynamicField : IDebugField  
```  
  
## 实现者说明  
 此接口由符号提供程序实现为可以在运行时确定的任何类型的基类。  这仅适用于托管代码。  
  
## 调用方的说明  
 此接口表示更专用接口可以派生的基类。  
  
## 方法按 Vtable 顺序  
 此接口不提供任何方法除了继承的参数以外从 `IDebugField`。  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [符号提供程序接口](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)