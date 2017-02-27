---
title: "IDebugPointerField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPointerField"
helpviewer_keywords: 
  - "IDebugPointerField 接口"
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPointerField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示指针类型。  
  
## 语法  
  
```  
IDebugPointerField : IDebugContainerField  
```  
  
## 实现者说明  
 符号提供程序实现此接口表示指针。  
  
## 调用方的说明  
 ，如果 [GetKind](../Topic/IDebugField::GetKind.md) 返回 `FIELD_TYPE_POINTER`，请使用 [QueryInterface](/visual-cpp/atl/queryinterface) 从 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 接口的此接口。  
  
## 方法按 Vtable 顺序  
 除了在 `IDebugField` 和 `IDebugContainerField` 接口的方法之外，此接口执行以下方法:  
  
|方法|说明|  
|--------|--------|  
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|返回描述指针的目标 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 。|  
  
## 备注  
 在 C\/C\+\+，则为; 如果使用数组表示法，指针可以是容器。  例如命名 `char *pString`， `pString` 具有指针的类型。 `char`。  `pString[3]` 具有是指向 `char` 引用该容器的第四个元素容器的类型。  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [符号提供程序接口](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)