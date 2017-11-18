---
title: "响应并且将更改传播 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, events
ms.assetid: fc2e9ac5-7a84-44ed-9945-94e45f89c227
caps.latest.revision: "24"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 7ea11c018f210b804f4ea6542eb7a7817ae1507c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="responding-to-and-propagating-changes"></a>响应并传播更改
元素是创建、 删除或更新时，你可以编写传播的更改的其他部分的模型，或对外部资源，如文件、 数据库或其他组件的代码。  
  
## <a name="in-this-section"></a>本节内容  
 作为一项准则，请考虑按以下顺序这些技术：  
  
|技术|方案|更多相关信息|  
|---------------|---------------|--------------------------|  
|定义计算域属性。|从模型中的其他属性计算其值的一个域属性。 例如，价格的价格之和的相关的元素。|[计算的和自定义的存储属性](../modeling/calculated-and-custom-storage-properties.md)|  
|定义自定义存储域属性。|存储在其他部分的模型或外部域属性。 例如，你无法将表达式字符串解析到模型中的一个树。|[计算的和自定义的存储属性](../modeling/calculated-and-custom-storage-properties.md)|  
|替代 OnDeleting OnValueChanging 等的更改处理程序|使不同的元素保持同步，并保留外部值与模型同步。<br /><br /> 约束定义的范围内的值。<br /><br /> 调用立即之前和之后属性值和其他更改。 可以通过引发异常终止更改。|[域属性值更改处理程序](../modeling/domain-property-value-change-handlers.md)|  
|规则|你可以定义将排队等待只需在发生更改事务结束之前执行的规则。 它们不会撤消或重做上执行。 使用它们来跟踪存储的一部分与另一个不同步。|[规则在模型内部传播更改](../modeling/rules-propagate-changes-within-the-model.md)|  
|存储事件|建模存储区提供通知的事件，例如添加或删除元素或链接，或更改属性的值。 该事件还将撤消和重做上执行。 使用应用商店事件以更新不存在于存储的值。|[事件处理程序在模型外部传播更改](../modeling/event-handlers-propagate-changes-outside-the-model.md)|  
|.NET 事件|形状具有响应鼠标单击和其他笔势的事件处理程序。 你必须将注册的这些事件的每个对象。 注册的重写中 InitializeInstanceResources，通常是，而且必须完成的每个元素。<br /><br /> 这些事件通常发生在事务之外。|[如何：截获对形状或修饰器的单击](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|  
|边界规则|边界规则专门用于约束形状的边界。|[BoundsRules 约束形状位置和大小](../modeling/boundsrules-constrain-shape-location-and-size.md)|  
|选择规则|选择规则专门限制用户可以选择。|[如何：访问和约束当前所选内容](../modeling/how-to-access-and-constrain-the-current-selection.md)|  
|OnAssocatedPropertyChanged|指示使用的形状和连接符如卷影、 箭头、 颜色和线条宽度和样式的功能的模型元素的状态。|[更新形状和连接线以反映模型](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|  
  
## <a name="comparing-rules-and-store-events"></a>**比较规则和存储事件**  
 在模型中发生更改时，将运行更改通告程序、 规则和事件。  
  
 在结束事务在其中已发生更改，通常应用规则并提交在事务中的更改后应用事件。  
  
 使用应用商店事件以同步模型与应用商店和规则，以保持在存储中的一致性之外的对象。  
  
-   **创建自定义规则**作为抽象规则从派生类创建自定义规则。 你还必须通知有关的自定义规则的框架。 有关详细信息，请参阅[规则传播更改内模型](../modeling/rules-propagate-changes-within-the-model.md)。  
  
-   **订阅事件**可以订阅事件之前，创建事件处理程序和委托。 然后使用<xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A>属性来订阅事件。 有关详细信息，请参阅[事件处理程序传播更改外部模型](../modeling/event-handlers-propagate-changes-outside-the-model.md)。  
  
-   **撤消更改**时撤消事务，引发的事件，但不是会应用规则。 将值更改为规则和撤消所做的更改，值将重置为原始值撤消操作期间。 当引发事件时，你必须手动更改回其原始值的值。 若要了解有关 transactons 和撤消的详细信息，请参阅[如何： 使用事务来更新模型](../modeling/how-to-use-transactions-to-update-the-model.md)。  
  
-   **传递给规则和事件的事件自变量**这两个事件和传递规则`EventArgs`参数，其中包含有关如何信息的模型更改。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 截获点击形状或修饰器](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)   
 [编写代码以自定义域特定语言](../modeling/writing-code-to-customise-a-domain-specific-language.md)