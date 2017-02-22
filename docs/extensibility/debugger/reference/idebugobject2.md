---
title: "IDebugObject2 | Microsoft Docs"
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
  - "IDebugObject2"
helpviewer_keywords: 
  - "IDebugObject2 接口"
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此接口提供的对象有关的其他信息。  
  
## 语法  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## 实施者注意事项  
 表达式计算器实现此接口以提供对别名和访问该对象有关的信息的支持。  
  
## 调用方的说明  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 接口通过使用可以获得此接口 [QueryInterface](/visual-cpp/atl/queryinterface)。 此外， [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) 返回此接口。  
  
## Vtable 顺序中的方法  
 除了上方法 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 接口， `IDebugObject2` 接口实现了下列︰  
  
|方法|描述|  
|--------|--------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|获取字段或变量 （如果有），可能会支持该对象表示的属性。|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|获取表示此对象的值的托管的代码对象。|  
|[CreateAlias](../Topic/IDebugObject2::CreateAlias.md)|创建此对象的唯一 ID，则返回该键的现有别名。|  
|[GetAlias](../Topic/IDebugObject2::GetAlias.md)|如果有的话，请获取与此对象关联的别名。|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|获取此对象的类型。|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|确定此对象是否表示用户数据。|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|确定是否编辑并继续状态将不再有效。<br /><br /> 自定义表达式计算器不实现此方法 \(应始终返回 `E_NOTIMPL`\)。|  
  
## 备注  
 请参阅 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) 有关别名的讨论。  
  
## 要求  
 标头︰ ee.h  
  
 命名空间 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 程序集 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [表达式计算接口](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)