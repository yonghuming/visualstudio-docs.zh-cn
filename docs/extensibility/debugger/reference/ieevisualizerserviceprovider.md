---
title: "IEEVisualizerServiceProvider |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEVisualizerServiceProvider
helpviewer_keywords: IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4bd55bb42f902bcda7cdef1ea28a8d1c39d96f26
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
>  在 Visual Studio 2015 中，已弃用这种方式实施表达式计算器。 有关实现 CLR 表达式计算器的信息，请参阅[CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此接口访问的可以创建一个可视化工具服务，它用于处理 IDE 类型可视化工具任务的方法。  
  
## <a name="syntax"></a>语法  
  
```  
IEEVisualizerServiceProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 Visual Studio 实现此接口可创建可视化工具服务对象，后者反过来用于提供类 Id (`CLSID`s) 的类型到 Visual Studio IDE 的可视化工具。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 表达式计算器 (EE) 调用[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)获取此接口。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|创建可视化工具服务|  
  
## <a name="remarks"></a>备注  
 `IEEVisualizerServiceProvider`过程的实现中获取接口[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)。 此接口创建的可视化工具服务用于提供功能[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)接口，EE 负责实现。 EE 程序还负责实现[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)允许类型可视化工具查看和修改属性的值的接口。  
  
 请参阅[Visualizing 和查看数据](../../../extensibility/debugger/visualizing-and-viewing-data.md)有关这些接口的交互方式的详细信息。  
  
## <a name="requirements"></a>要求  
 标头： ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [表达式评估接口](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [可视化和查看数据](../../../extensibility/debugger/visualizing-and-viewing-data.md)