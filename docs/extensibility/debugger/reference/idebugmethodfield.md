---
title: "IDebugMethodField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField"
helpviewer_keywords: 
  - "IDebugMethodField 接口"
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugMethodField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口描述一个方法。  
  
## 语法  
  
```  
IDebugMethodField : IDebugContainerField  
```  
  
## 实现者说明  
 符号提供程序实现在同一对象的此接口实现 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 接口。  此接口存在一个方法的专用化。  
  
## 调用方的说明  
 ，如果 [GetKind](../Topic/IDebugField::GetKind.md) 返回 `FIELD_TYPE_METHOD`，请使用 [QueryInterface](/visual-cpp/atl/queryinterface) 从 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 接口的此接口。  此外，方法、 [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)、 [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)和 [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)，都返回 `IDebugMethodField` 接口。  
  
## 方法按 Vtable 顺序  
 除了在 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 和 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 接口的方法之外，此接口执行以下方法:  
  
|方法|说明|  
|--------|--------|  
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|创建方法的参数的枚举数。|  
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|获取包含方法的对象的 “this”指针。|  
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|创建方案中的所有局部变量的枚举数。|  
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|创建方法的选定的局部变量的枚举数。|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|确定某一给定自定义属性是否定义了。|  
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|创建方法的静态局部变量的枚举数。|  
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|获取方法的全局容器。|  
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|创建所需的每个参数的类型的枚举器调用方法。|  
  
## 备注  
 方案可以包含参数和局部变量。  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [符号提供程序接口](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)