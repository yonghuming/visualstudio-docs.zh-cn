---
title: "InvokeMethod 活动设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8d84873c1d4755b4eea723345f52d71064ecb9ab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="invokemethod-activity-designer"></a>InvokeMethod 活动设计器
**InvokeMethod**设计器用于创建和配置<xref:System.Activities.Statements.InvokeMethod>活动。  
  
## <a name="the-invokemethod-activity"></a>InvokeMethod 活动  
 <xref:System.Activities.Statements.InvokeMethod> 调用指定对象或类型的公共方法。  
  
### <a name="using-the-invokemethod-activity-designer"></a>使用 InvokeMethod 活动设计器  
 **InvokeMethod**在找不到活动设计器**基元**类别**工具箱**，通过单击访问的哪一**工具箱**选项卡[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，选择**工具栏**从**视图**菜单上或 CRTL + ALT + X。)  
  
 **InvokeMethod**活动设计器可以拖动从**工具箱**拖放到[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]图面任何位置通常放置活动的如内<xref:System.Activities.Statements.Sequence>。 这将创建具有 InvokeMethod 的默认 <xref:System.Activities.Statements.InvokeMethod> 的 <xref:System.Activities.Activity.DisplayName%2A> 活动。 <xref:System.Activities.Activity.DisplayName%2A>可以在的标头中编辑**InvokeMethod**活动设计器中或在**DisplayName**属性网格的框。  
  
### <a name="the-invokemethod-properties"></a>InvokeMethod 属性  
 下表列出 <xref:System.Activities.Statements.InvokeMethod> 属性并说明如何在设计器中使用它们。 这些属性可以在属性网格中进行编辑，其中一些属性还可以在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 设计器图面上进行编辑。  
  
|属性名|必需|用法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.InvokeMethod> 活动的友好名称。 默认值为 InvokeMethod。<br /><br /> 虽然 <xref:System.Activities.Activity.DisplayName%2A> 不是绝对必需的，但最好使用该属性。|  
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|要在执行活动时调用的方法的名称。 调用的方法必须声明为**公共**。 此属性可以在设计器图面上进行编辑。 此属性是强制属性。|  
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|所调用方法的参数集合。 将参数添加到集合中的顺序必须与这些参数在方法签名中出现的顺序相同。 在属性网格中，单击中的省略号按钮**参数**字段，它显示**参数**对话框以便您设置此属性。 单击**创建自变量**按钮以添加参数。|  
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|方法调用的返回值。|  
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|指定是否异步调用该方法。 默认值是**False**。|  
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|包含要调用的方法的对象。 此属性可以在设计器图面上进行编辑。<br /><br /> 必须设置 <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 或 <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> 之一。|  
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 的类型。 此属性可以在设计器图面上进行编辑。 只有当调用的方法为静态时，才必须设置此属性。|  
  
 若要将参数传递为 C#**出**参数 (例如，`Method1(out myParam)),`应使用**OutArgument**而不是**InOutArgument**  
  
 使用自变量调用**TargetObject**或**结果**不能调用使用<xref:System.Activities.Statements.InvokeMethod>活动。 原因是 <xref:System.Activities.Statements.InvokeMethod> 活动在 <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> 中注册 <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>、<xref:System.Activities.Statements.InvokeMethod.Result%2A> 和 <xref:System.Activities.Activity.CacheMetadata%2A>。  
  
 在 <xref:System.Activities.Activity.CacheMetadata%2A> 中注册这些参数的算法如下所列：  
  
1.  注册 <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 参数。  
  
2.  注册 <xref:System.Activities.Statements.InvokeMethod.Result%2A> 参数。  
  
3.  循环访问 <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> 集合并注册每个参数。  
  
 产生的异常的类型为 <xref:System.Activities.InvalidWorkflowException> 并带有以下消息：“InvokeMethod”: 已存在名为“TargetObject”的变量、RuntimeArgument 或 DelegateArgument。 在环境作用域中，名称必须唯一。  
  
 此限制不适用于 <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> 和 <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>，因为它们不是工作流参数，因此在 <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> 方法中而不在 <xref:System.Activities.Statements.InvokeMethod> 活动的 <xref:System.Activities.Activity.CacheMetadata%2A> 集合中注册。  
  
## <a name="see-also"></a>另请参阅  
 [基元](../workflow-designer/primitives-activity-designers.md)   
 [分配](../workflow-designer/assign-activity-designer.md)   
 [延迟](../workflow-designer/delay-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)