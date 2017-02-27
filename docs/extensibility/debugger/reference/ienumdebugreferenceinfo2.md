---
title: "IEnumDebugReferenceInfo2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugReferenceInfo2"
helpviewer_keywords: 
  - "IEnumDebugReferenceInfo2"
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugReferenceInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口枚举 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 结构。  
  
## 语法  
  
```  
IEnumDebugReferenceInfo2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎 \(DE\)实现此接口作为其一部分支持对内存中的对象。  此接口，仅当引用支持，必须实现。  
  
## 调用方的说明  
 Visual Studio 会调用 [EnumChildren](../Topic/IDebugReference2::EnumChildren.md) 获取此接口。  
  
## 方法按 Vtable 顺序  
 下表显示 `IEnumDebugReferenceInfo2`方法。  
  
|方法|说明|  
|--------|--------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|检索 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 结构指定数目的枚举序列的。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|跳过 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 结构指定数目的枚举序列的。|  
|[重置](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|重置枚举序列与开头。|  
|[克隆](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|创建包含枚举状态和枚举当前枚举数相同的枚举数。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|获取 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 结构数在枚举数。|  
  
## 备注  
 引用实质上是类型和地址，，而属性是名称、类型和地址。  ，只要引用的对象存在于内存，引用仍然存在。  有关详细信息，请参见 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [EnumChildren](../Topic/IDebugReference2::EnumChildren.md)