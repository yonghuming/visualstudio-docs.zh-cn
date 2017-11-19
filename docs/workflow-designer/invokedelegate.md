---
title: "InvokeDelegate |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: "3"
ms.author: sdanie
manager: erikre
ms.openlocfilehash: 180e9ca5ae635608ca3d7f9cf24abab13c8076a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="invokedelegate"></a>InvokeDelegate
**InvokeDelegate**设计器用于创建和配置<xref:System.Activities.Statements.InvokeDelegate>活动。  
  
## <a name="the-invokedelegate-activity"></a>InvokeDelegate 活动  
 <xref:System.Activities.Statements.InvokeDelegate> 调用公共委托。  
  
### <a name="using-the-invokedelegate-activity-designer"></a>使用 InvokeDelegate 活动设计器  
 **InvokeDelegate**在找不到活动设计器**基元**类别**工具箱**，通过单击访问的哪一**工具箱**选项卡[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，选择**工具栏**从**视图**菜单上或 CRTL + ALT + X。)  
  
 **InvokeDelegate**活动设计器可以拖动从**工具箱**拖放到[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]图面任何位置通常放置活动的如内<xref:System.Activities.Statements.Sequence>。 这将创建具有 InvokeDelegate 的默认 <xref:System.Activities.Statements.InvokeDelegate> 的 <xref:System.Activities.Activity.DisplayName%2A> 活动。 <xref:System.Activities.Activity.DisplayName%2A>可以在的标头中编辑**InvokeDelegate**活动设计器中或在**DisplayName**属性网格的框。  
  
### <a name="the-invokedelegate-properties"></a>InvokeDelegate 属性  
 下表列出 <xref:System.Activities.Statements.InvokeDelegate> 属性并说明如何在设计器中使用它们。 这些属性可以在属性网格中进行编辑，其中一些属性还可以在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 设计器图面上进行编辑。  
  
|属性名|必需|用法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.InvokeDelegate> 活动的友好名称。 默认值为 InvokeDelegate。<br /><br /> 虽然 <xref:System.Activities.Activity.DisplayName%2A> 不是绝对必需的，但最好使用该属性。|  
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|要在执行活动时调用的 <xref:System.Activities.ActivityDelegate> 的名称。 此属性可以在设计器图面上进行编辑。 此属性是强制属性。|  
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|调用委托的自变量集合。 密钥的参数对象的名称位于<xref:System.Activities.ActivityDelegate>和值是其表达式将进行计算并分配给相应的参数对象的参数。 在属性网格中，单击中的省略号按钮**DelegateArguments**字段，它显示**DelegateArguments**对话框以便您设置此属性。 单击**创建自变量**字段以添加参数。|  
  
## <a name="see-also"></a>另请参阅  
 [如何：在工作流设计器中定义和使用活动委托](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)