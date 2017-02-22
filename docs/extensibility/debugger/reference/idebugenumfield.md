---
title: "IDebugEnumField | Microsoft Docs"
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
  - "IDebugEnumField"
helpviewer_keywords: 
  - "IDebugEnumField 接口"
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEnumField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示枚举类型。  
  
## 语法  
  
```  
IDebugEnumField : IDebugContainerField  
```  
  
## 实现者说明  
 符号提供程序实现此接口表示枚举。  
  
## 调用方的说明  
 ，如果 [GetKind](../Topic/IDebugField::GetKind.md) 返回 `FIELD_TYPE_ENUM`，请使用 [QueryInterface](/visual-cpp/atl/queryinterface) 从 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 接口的此接口。  
  
## 方法按 VTable 顺序  
 除了在 `IDebugField` 和 `IDebugContainerField` 接口的方法之外，此接口执行以下方法:  
  
|方法|说明|  
|--------|--------|  
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|返回描述名称此枚举类型的 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 。|  
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|返回枚举常量的名称与该特定值。|  
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|返回值与给定的枚举常量名称|  
|[GetValueFromStringCaseInsensitive](../Topic/IDebugEnumField::GetValueFromStringCaseInsensitive.md)|返回值与特定枚举常量名称，但忽略大小写。|  
  
## 备注  
 它是实际绑定到具有 [将绑定](../../../extensibility/debugger/reference/idebugbinder-bind.md)的位置的基础符号。  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [符号提供程序接口](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [将绑定](../../../extensibility/debugger/reference/idebugbinder-bind.md)