---
title: "实现类型可视化工具和自定义查看器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 19718425df6f0c8a656db0e3d7ebf0f06937f780
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-type-visualizers-and-custom-viewers"></a>实现类型可视化工具和自定义查看器
> [!IMPORTANT]
>  在 Visual Studio 2015 中，已弃用这种方式实施表达式计算器。 有关实现 CLR 表达式计算器的信息，请参阅[CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 类型可视化工具和自定义查看器允许用户查看程序比简单的十六进制转储的数字更有意义的方式中的特定类型的数据。 表达式计算器 (EE) 可以将自定义查看器与特定类型的数据或变量相关联。 由 EE 实现这些自定义查看器。 EE 还可以支持外部类型的可视化工具，可能来自于另一个第三方供应商或甚至最终用户。  
  
## <a name="discussion"></a>讨论  
  
### <a name="type-visualizers"></a>类型可视化工具  
 Visual Studio 会要求有关类型可视化工具以及为每个对象的自定义查看器将在监视窗口中显示的列表。 表达式计算器 (EE) 提供此类列表的每种类型它想要支持类型可视化工具和自定义查看器。 调用[GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)和[GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)开始整个过程的访问类型可视化工具和自定义查看器 (请参阅[Visualizing 和查看数据](../../extensibility/debugger/visualizing-and-viewing-data.md)有关调用的序列的详细信息)。  
  
### <a name="custom-viewers"></a>自定义查看器  
 自定义查看器在特定的数据类型为 EE 中实现，由表示[IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)接口。 自定义查看器不是灵活性不如类型可视化工具，因为仅当执行 EE 实现该特定的自定义查看器，它才可用。 实现自定义查看器是更简单，而不是实现类型可视化工具的支持。 但是，支持类型可视化工具可以提供最大的灵活性向最终用户可视化他或她的数据。 本文的讨论的其余部分涉及仅类型可视化工具。  
  
## <a name="interfaces"></a>接口  
 EE 实现了以下接口来支持类型可视化工具，可供 Visual Studio:  
  
-   [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
-   [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
-   [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
-   [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
-   [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
 EE 使用了以下接口来支持类型可视化工具：  
  
-   [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
-   [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
-   [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## <a name="see-also"></a>另请参阅  
 [编写 CLR 表达式计算器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [可视化和查看数据](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)