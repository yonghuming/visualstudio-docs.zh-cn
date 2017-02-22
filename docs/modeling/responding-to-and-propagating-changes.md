---
title: "响应并传播更改 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "域特定语言, 事件"
ms.assetid: fc2e9ac5-7a84-44ed-9945-94e45f89c227
caps.latest.revision: 24
caps.handback.revision: 24
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 响应并传播更改
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在元素后，删除或更新时，可以传播到设计的其他部分的更改编写代码，或对外部资源 \(如文件、数据库，或其他元素。  
  
## 本节内容  
 一般原则是，请考虑按以下顺序的以下技术:  
  
|方法|方案|更多信息|  
|--------|--------|----------|  
|定义一个计算的字段的特性。|值从在设计的其他属性计算的字段的特性。  例如，相关元素的价格的总和的价格。|[计算的和自定义存储属性](../modeling/calculated-and-custom-storage-properties.md)|  
|定义自定义存储字段的特性。|在设计的外部其他部分中的字段或属性。  例如，可以分析表达式字符串到设计的一个树。|[计算的和自定义存储属性](../modeling/calculated-and-custom-storage-properties.md)|  
|重写更改处理程序 \(如 OnValueChanging 和 OnDeleting|使不同的同步的组件，并保留外部值与设计保持同步。<br /><br /> 绑定值设置为定义的范围内。<br /><br /> 调用之前直接与属性值和其他后更改。  可以通过引发异常终止更改。|[域属性值更改处理程序](../modeling/domain-property-value-change-handlers.md)|  
|规则|可以定义为事务之前结束的执行排队发生更改的规则。  它们在 Undo 或 Redo 不会执行。  使用它们只存储的一部分与另一个的不同步。|[规则将在模型中的更改传播](../modeling/rules-propagate-changes-within-the-model.md)|  
|存储事件|建模存储提供事件的通知如添加或删除元素或链接或更改属性的值。  事件在撤消和 Redo 也会执行。  用于存储事件更新不在存储的值。|[事件处理程序在模型外部传播更改](../modeling/event-handlers-propagate-changes-outside-the-model.md)|  
|.NET 事件|形状具有响应鼠标单击和其他操作的事件处理程序。  必须这些事件注册每个对象的。  注册在 InitializeInstanceResources 重写通常完成，并且必须为每个元素执行。<br /><br /> 这些事件在事务外通常发生。|[如何：截获对形状或修饰器的单击](../Topic/How%20to:%20Intercept%20a%20Click%20on%20a%20Shape%20or%20Decorator.md)|  
|区域规则|区域规则专门用于约束形状的区域。|[BoundsRules 约束形状位置和大小](../modeling/boundsrules-constrain-shape-location-and-size.md)|  
|选中该规则|选中该规则专门约束哪些用户可以选择。|[如何：访问和约束当前所选内容](../modeling/how-to-access-and-constrain-the-current-selection.md)|  
|OnAssocatedPropertyChanged|使用形状功能和连接例如阴影，指示模型元素的状态、箭头、颜色和线宽和样式。|[更新形状和连接线以反映模型](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|  
  
## **比较规则和存储事件**  
 更改通告方，规则，因此，事件运行，更改在设计时发生。  
  
 规则通常是应用程序的发生更改的结束事务，因此，事件的应用，在事务中的进行更改后。  
  
 用于存储事件与在存储外的对象同步模型和规则维护存储区中的一致性。  
  
-   **创建自定义规则** 您创建自定义规则作为派生的类从一个抽象规则。  您还必须通知自定义规则集的结构。  有关更多信息，请参见 [规则将在模型中的更改传播](../modeling/rules-propagate-changes-within-the-model.md)。  
  
-   **订阅事件** ，然后才能订阅事件之前，创建事件处理程序和委托。  然后使用 <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A>属性订阅事件。  有关更多信息，请参见 [事件处理程序在模型外部传播更改](../modeling/event-handlers-propagate-changes-outside-the-model.md)。  
  
-   **撤消更改** ，当您撤消事务，则会引发事件，但是，规则不适用。  如果规则更改值，并且您无法撤消所做的更改，该值被重置为原始值将取消操作时。  引发事件时，必须手动更改该值返回到其原始值。  若要了解更多信息 transactons 和取消，请参见 [如何：使用事务更新模型](../modeling/how-to-use-transactions-to-update-the-model.md)。  
  
-   **传递事件参数对规则和** 事件和规则传递具有有关的 `EventArgs` 参数该模型如何的信息已更改。  
  
## 请参阅  
 [如何：截获对形状或修饰器的单击](../Topic/How%20to:%20Intercept%20a%20Click%20on%20a%20Shape%20or%20Decorator.md)   
 [编写代码以自域特定语言](../modeling/writing-code-to-customise-a-domain-specific-language.md)