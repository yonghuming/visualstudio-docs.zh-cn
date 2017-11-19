---
title: "键入可视化工具和自定义查看器 |Microsoft 文档"
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
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 80798887beee6116b3a93b5d8ec86b14269b5475
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="type-visualizer-and-custom-viewer"></a>类型可视化工具和自定义查看器
类型可视化工具是非常特定的格式显示一段数据的组件。 这种格式可以完全取决于实施者的可视化工具，最终用户或第三方供应商的可视化工具是它。  
  
 自定义查看器是非常特定的格式显示一段数据自定义表达式计算器的一部分。 这种格式可以完全取决于实施者的自定义查看器中，这意味着格式取决于实施者的表达式计算器 (EE)。  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>表达式计算器中的类型可视化工具的支持  
 EE 可以通过支持一套可视化工具可以访问的接口来支持类型可视化工具： 如接口[IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)和[IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)。 但请注意，EE 概不负责实现类型可视化工具本身： EE 只允许外部可视化工具对其类型信息的访问。 此类可视化工具可能传送以及 EE，和可以安装在 Visual Studio 中，由另一个第三方供应商或甚至最终用户提供的适当位置。  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>表达式计算器中的自定义查看器的支持  
 EE 还可以支持自定义查看器在其中 EE 本身提供的代码查看的数据类型。 自定义查看器实现[IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)接口，用于处理的任何格式显示数据的所有职责所需; 查看器可以显示的完全控制，甚至还可以允许要修改的数据。 由 EE 提供任何自定义查看器附带 EE 发货产品时。  
  
## <a name="see-also"></a>另请参阅  
 [调试器组件](../../extensibility/debugger/debugger-components.md)   
 [表达式计算器](../../extensibility/debugger/expression-evaluator.md)   
 [调试引擎](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)