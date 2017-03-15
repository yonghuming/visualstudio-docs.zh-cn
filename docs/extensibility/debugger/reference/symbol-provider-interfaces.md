---
title: "符号提供程序接口 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "接口，符号处理程序"
  - "符号处理程序中接口"
  - "符号处理程序中，计算变量的值"
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# 符号提供程序接口
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

下面是处理 [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]的符号接口。  
  
## 讨论  
 在中断模式下，这些接口用于计算调用堆栈上的变量。  对公共语言运行时符号提供程序只实现 \(SP\)。  
  
|接口|实现|说明|  
|--------|--------|--------|  
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|表示项目的地址。|  
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|表示项目的地址，提供对进程 ID.|  
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|表示数组符号或数组类型。|  
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|表示类符号或类类型。|  
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|用特定于托管代码的方法表示 COM\+ 符号提供程序。|  
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|用特定于托管代码的方法表示 COM\+ 符号提供程序和扩展 **IDebugComPlusSymbolProvider**。|  
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|表示其他符号或类型的容器的符号或类型。|  
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|表示可附加到符号的自定义特性。|  
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|表示自定义属性的查询在方法或类型。|  
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|在符号提供对自定义特性。|  
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|可以在运行时确定的任何类型的基接口。|  
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|表示 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 对象的动态字段。|  
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|表示枚举类型。|  
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|Sp|扩展可用字段的类型支持托管代码型。|  
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|所有字段的基类;表示符号或类型的声明。|  
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|表示一个字段的定义托管代码泛型类型的。|  
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|表示一个字段的实例托管代码泛型类型的。|  
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|表示托管代码泛型类型的参数。|  
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|表示。|  
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|表示调试选项修饰符。|  
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|表示指针。|  
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|表示基元类型从 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 接口的枚举值。|  
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|表示可以作为获取或设置托管代码类的属性。|  
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|表示提供符号和类型的符号提供程序。|  
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|无需直接访问表示符号提供程序将元数据和内核符号接口。|  
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|表示能够创建表示类型的字段。|  
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|扩展 **IDebugTypeFieldBuilder** 可以创建数组类型。|  
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|表示 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 对象的集合。|  
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|表示 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) 对象的集合。|  
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|表示 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 对象的集合。|  
  
## 请参阅  
 [API 参考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)