---
title: "自定义元素工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 6
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 6
---
# 自定义元素工具
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在某些 DSL 定义中，作为一组元素表示在一个概念。 例如，如果创建其中一个组件具有一组固定的端口的一个模型，您始终想要在其父组件在同一时间创建的端口。 因此，您必须自定义的元素创建工具，使其创建一组而不仅仅是一个元素。 若要实现此目的，您可以自定义如何初始化的元素创建工具。  
  
 您还可以重写该工具拖动到关系图或一个元素上会发生什么情况。  
  
## 自定义的一种元素工具的内容  
 每个元素工具存储的实例 <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> \(EGP\)，其中包含一个或多个模型元素和链接的序列化的版本。 默认情况下，一种元素工具 EGP 包含一个指定该工具的类的实例。 您可以通过重写中更改此 *YourLanguage*`ToolboxHelper.CreateElementToolPrototype`。 DSL 包加载时，调用此方法。  
  
 方法的一个参数是类的在 DSL 定义中指定的 ID。 当替换您感兴趣的类调用方法时，您可以将额外的元素添加到 EGP。  
  
 EGP 必须包括嵌入附属元素从一个主要元素的链接。 它还可以包含引用链接。  
  
 下面的示例创建主要元素和两个嵌入的元素。 主类称为电阻器，并具有两个名为终端的元素的嵌入关系。 嵌入的角色属性分别名为 Terminal1 和 Terminal2，而且它们都具有重数为 1..1。  
  
```  
using Microsoft.VisualStudio.Modeling; ...    
public partial class CircuitDiagramToolboxHelper  
{  
  protected override ElementGroupPrototype    CreateElementToolPrototype(Store store, Guid domainClassId)  
  {  
    // A case for each tool to customize:    
    if (domainClassId == Resistor.DomainClassId)  
    {  
      // Set up the prototype elements and links:  
      Resistor resistor = new Resistor(store);  
      resistor.Terminal1 = new Terminal(store);   
      resistor.Terminal2 = new Terminal(store);  
      resistor.Terminal1.Name = "T1"; // embedding  
      resistor.Terminal2.Name = "T2"; // embedding  
      // We could also set up reference links.  
  
      // Create an element group prototype for the toolbox:  
      ElementGroup egp = new ElementGroup(store.DefaultPartition);  
      egp.AddGraph(resistor, true);  
      // We do not have to explicitly include embedded children.  
      return egp.CreatePrototype();  
    }  
    // Element tools for other classes:  
    else  
      return base.CreateElementToolPrototype(store, domainClassId);  
  }  
}  
```  
  
## 请参阅  
 [自定义元素创建和移动](../modeling/customizing-element-creation-and-movement.md)