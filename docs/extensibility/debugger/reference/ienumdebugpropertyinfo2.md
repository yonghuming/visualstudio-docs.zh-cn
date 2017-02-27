---
title: "IEnumDebugPropertyInfo2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPropertyInfo2"
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo2"
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugPropertyInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口枚举 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 结构。  
  
## 语法  
  
```  
IEnumDebugPropertyInfo2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎 \(DE\)实现此接口表示特定属性的信息。  
  
## 调用方的说明  
 调用 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 获取表示特定属性的子此接口。  调用 [EnumProperties](../Topic/IDebugStackFrame2::EnumProperties.md) 获取表示特定堆栈帧的属性的此接口。  
  
## 方法按 Vtable 顺序  
 下表显示 `IEnumDebugPropertyInfo2`方法。  
  
|方法|说明|  
|--------|--------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|检索 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 结构指定数目的枚举序列的。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|跳过 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 结构指定数目的枚举序列的。|  
|[重置](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|重置枚举序列与开头。|  
|[克隆](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|创建包含枚举状态和枚举当前枚举数相同的枚举数。|  
|[GetCount](../Topic/IEnumDebugPropertyInfo2::GetCount.md)|获取 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 结构数在枚举数。|  
  
## 备注  
 通常，属性是可以包括名称，值，解决信息和类型的层次结构，以及其他信息适用于关联的属性对象或堆栈帧。  有关详细信息，请参见 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../Topic/IDebugStackFrame2::EnumProperties.md)