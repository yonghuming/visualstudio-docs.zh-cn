---
title: "IEnumDebugCustomAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumCustomAttributes"
helpviewer_keywords: 
  - "IEnumDebugCustomAttributes 接口"
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IEnumDebugCustomAttributes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

枚举自定义特性。  
  
## 语法  
  
```  
IEnumCustomAttributes : IUnknown  
```  
  
## 实现者说明  
 符号提供程序实现此接口支持自定义特性 \(通过 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) 接口\)。  
  
## 调用方的说明  
 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) 返回此接口。  
  
## 方法按 Vtable 顺序  
 下表显示 `IEnumDebugCustomAttributes`方法。  
  
|方法|说明|  
|--------|--------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|检索自定义特性指定数目的枚举序列的。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|跳过自定义特性指定数目的枚举序列的。|  
|[重置](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|重置枚举序列与开头。|  
|[克隆](../Topic/IEnumDebugCustomAttributes::Clone.md)|创建包含枚举状态和枚举当前枚举数相同的枚举数。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|获取自定义属性数在枚举数。|  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [符号提供程序接口](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)   
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)