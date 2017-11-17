---
title: "自定义元素工具 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: "6"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 2555fe2be42ed58482cdacf174a6cb035a8d7bd5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="customizing-element-tools"></a>自定义元素工具
在某些 DSL 定义，作为一组元素表示在一个概念。 例如，如果你创建在其中一个组件具有一组固定的端口的一个模型，你始终希望要在其父组件在同一时间创建的端口。 因此，你必须自定义的元素创建工具，以便它创建的一组而并非仅仅一个元素。 若要实现此目的，你可以自定义如何初始化元素创建工具。  
  
 你还可以重写该工具拖动到关系图或元素上时，会发生什么情况。  
  
## <a name="customizing-the-content-of-an-element-tool"></a>自定义的一种元素工具的内容  
 每个元素工具将存储的实例<xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>(EGP)，其中包含一个或多个模型元素和链接的序列化的版本。 默认情况下，一种元素工具 EGP 包含该工具的指定类的一个实例。 您可以通过重写中更改此*YourLanguage*`ToolboxHelper.CreateElementToolPrototype`。 DSL 包加载时，调用此方法。  
  
 方法的一个参数是类的 DSL 定义中指定的 ID。 当与你感兴趣的类调用方法时，也可以将额外的元素添加到 EGP。  
  
 EGP，必须包括嵌入从一个主要元素到子公司元素的链接。 它还可以包含引用的链接。  
  
 下面的示例创建一个主要元素和两个嵌入的元素。 主类称为电阻器，，它具有名为终端的元素的两个嵌入关系。 嵌入的角色属性名为 Terminal1 和 Terminal2，并且两者都 1..1 的重数。  
  
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
  
## <a name="see-also"></a>另请参阅  
 [自定义元素创建和移动](../modeling/customizing-element-creation-and-movement.md)