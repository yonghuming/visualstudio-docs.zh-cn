---
title: "IEnumDebugFields | Microsoft Docs"
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
  - "IEnumDebugFields"
helpviewer_keywords: 
  - "IEnumDebugFields 接口"
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugFields
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示实现 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 接口的对象的集合。  
  
## 语法  
  
```  
IEnumDebugFields : IUnknown  
```  
  
## 实现者说明  
 此接口由符号提供程序实现提供了一组对象实现 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 接口。  注意不是标准 COM 枚举由于 [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) 方法的显示。  
  
## 调用方的说明  
 此接口由 [GetMethodFieldsByName](../Topic/IDebugSymbolProvider::GetMethodFieldsByName.md) 和 [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)返回。  
  
## 方法按 Vtable 顺序  
 此接口执行以下操作方法。  
  
|方法|说明|  
|--------|--------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|枚举检索下一组 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 对象。|  
|[Skip](../Topic/IEnumDebugFields::Skip.md)|跳过项指定数目的。|  
|[重置](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|重置枚举先 enter。|  
|[克隆](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|检索当前枚举的副本。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|检索项数在枚举的。|  
  
## 备注  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [符号提供程序接口](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetMethodFieldsByName](../Topic/IDebugSymbolProvider::GetMethodFieldsByName.md)   
 [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)