---
title: "IEEVisualizerDataProvider |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEVisualizerDataProvider
helpviewer_keywords: IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9ffe7e33b4652c0f0d3bd506e28d14c5b0949983
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
>  在 Visual Studio 2015 中，已弃用这种方式实施表达式计算器。 有关实现 CLR 表达式计算器的信息，请参阅[CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此接口提供能够更改通过类型可视化工具的对象的值。  
  
## <a name="syntax"></a>语法  
  
```  
IEEVisualizerDataProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 表达式计算器实现此接口可通过类型可视化工具属性对象上支持修改数据。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 此接口可用于创建[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)对象，通过调用[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)。 请参阅[Visualizing 和查看数据](../../../extensibility/debugger/visualizing-and-viewing-data.md)有关详细信息。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|方法|描述|  
|------------|-----------------|  
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|确定是否可以更新此对象 （或随后，其值），表示此可视化工具。|  
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|为此可视化工具强制重新评估的对象。|  
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|获取此可视化工具 （完成任何评估） 的现有对象。|  
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|此可视化工具，从而更改可视化工具显示的值更新对象。|  
  
## <a name="remarks"></a>备注  
 可视化工具服务 (由表示[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)接口，并返回[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) 都会保留对对象实现引用`IEEVisualizerDataProvider`接口. 因此，`IEEVisualizerDataProvider`不应实现的相同对象上实现接口[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)如果该对象保留的引用`IEEVisualizerService`对象： 循环引用结果和当对象被销毁时，将发生死锁。 建议的方法是实现`IEEVisualizerDataProvider`到一个单独的对象上`IDebugProperty2`对象而不调用的委托`IUnknown::AddRef`在其上。  
  
## <a name="requirements"></a>要求  
 标头： ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [表达式评估接口](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [可视化和查看数据](../../../extensibility/debugger/visualizing-and-viewing-data.md)