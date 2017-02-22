---
title: "IDebugClassField | Microsoft Docs"
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
  - "IDebugClassField"
helpviewer_keywords: 
  - "IDebugClassField 接口"
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugClassField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示类为类型。  
  
## 语法  
  
```  
IDebugClassField : IDebugContainerField  
```  
  
## 实现者说明  
 符号提供程序实现在同一对象的此接口实现 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 接口。  此接口是表示类类型的专用化。  
  
## 调用方的说明  
 给定数的接口会返回此接口包括 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)、 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)和 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)的方法。  此外， [GetKind](../Topic/IDebugField::GetKind.md) ，如果方法返回标志 `FIELD_TYPE_CLASS`，可以使用 [QueryInterface](/visual-cpp/atl/queryinterface) 从 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 接口的此接口。  
  
## 方法按 Vtable 顺序  
 除了在 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 和 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 接口的方法之外，此接口实现了下列功能:  
  
|方法|说明|  
|--------|--------|  
|[EnumBaseClasses](../Topic/IDebugClassField::EnumBaseClasses.md)|创建此类的基类的枚举数。|  
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|确定特定接口是否在类中定义。|  
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|创建此类嵌套类的枚举数。|  
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|获取包含此类的类。|  
|[EnumInterfacesImplemented](../Topic/IDebugClassField::EnumInterfacesImplemented.md)|创建此类实现的接口的枚举数。|  
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|创建此类的构造函数的枚举数。|  
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|获取默认索引器的名称。|  
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|创建此类的嵌套枚举的枚举数。|  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [符号提供程序接口](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)