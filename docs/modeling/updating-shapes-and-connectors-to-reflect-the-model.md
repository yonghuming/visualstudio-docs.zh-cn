---
title: "更新形状和连接线以反映模型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51eb2af9-00e7-4725-a87d-62fb4f39f444
caps.latest.revision: 6
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: eb2ab9d49cdeb1ed71da8ef67841f7796862dc30
ms.openlocfilehash: 97ec749c0a89dae6c5a98702926d8ad82b6af3ac
ms.lasthandoff: 02/22/2017

---
# <a name="updating-shapes-and-connectors-to-reflect-the-model"></a>更新形状和连接线以反映模型
在域特定语言[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，可以使形状反映基础模型的状态的外观。  
  
 本主题中的代码示例应添加到`.cs`文件，在您`Dsl`项目。 你将需要每个文件中的这些语句︰  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  
```  
  
## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>设置形状映射属性来控制修饰器的可见性  
 您可以控制修饰器的可见性，而无需编写程序代码中，通过在 DSL 定义中配置该形状及与其域类之间的映射。 有关详细信息，请参阅 [如何定义 Domain-specific Language](../modeling/how-to-define-a-domain-specific-language.md)。
  
## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>将作为属性公开的颜色和形状的样式  
 在 DSL 定义中，右键单击形状类、 指向**公开添加**，然后单击某一项诸如**填充颜色**。  
  
 现在，该形状具有您可以在程序代码中或作为用户设置 domain 属性。 例如，若要将其设置的命令或规则的程序代码中，您可以编写︰  
  
 `shape.FillColor = System.Drawing.Color.Red;`  
  
 如果您想要使该属性变量仅在程序控制下并不是由用户，选择新的域属性，如**填充颜色**在 DSL 定义关系图中。 然后，在属性窗口中设置**可浏览**到`false`，或者设置**是 UI Readonly**到`true`。  
  
## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>定义更改规则，以使颜色、 样式或位置取决于模型元素属性  
 你可以定义更新的外观取决于模型的其他部分的形状的规则。 例如，您可以更新它依赖于模型元素的属性的形状的颜色的模型元素上定义更改规则。 有关更改规则的详细信息，请参阅[规则传播的更改中的模式](../modeling/rules-propagate-changes-within-the-model.md)。  
  
 您应使用规则仅用于更新在应用商店，会被保留下来的属性，因为执行撤消命令时，不会调用规则。 这不包括某些图形功能，例如大小和形状的可见性。 若要更新这些形状的功能，请参阅[更新非存储图形功能](#OnAssociatedProperty)。  
  
 下面的示例假定您已公开`FillColor`作为域属性上一节中所述。  
  
```c#  
[RuleOn(typeof(ExampleElement))]  
  class ExampleElementPropertyRule : ChangeRule  
  {  
    public override void ElementPropertyChanged(ElementPropertyChangedEventArgs e)  
    {  
      base.ElementPropertyChanged(e);  
      ExampleElement element = e.ModelElement as ExampleElement;  
      // The rule is called for every property that is updated.  
      // Therefore, verify which property changed:  
      if (e.DomainProperty.Id == ExampleElement.NameDomainPropertyId)  
      {  
        // There is usually only one shape:  
        foreach (PresentationElement pel in PresentationViewsSubject.GetPresentation(element))  
        {  
          ExampleShape shape = pel as ExampleShape;  
          // Replace this with a useful condition:  
          shape.FillColor = element.Name.EndsWith("3")   
                     ? System.Drawing.Color.Red : System.Drawing.Color.Green;  
        }  
      }  
    }  
  }  
  // The rule must be registered:  
  public partial class OnAssociatedPropertyExptDomainModel  
  {  
    protected override Type[] GetCustomDomainModelTypes()  
    {  
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
      types.Add(typeof(ExampleElementPropertyRule));  
      // If you add more rules, list them here.   
      return types.ToArray();  
    }  
  }  
  
```  
  
## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>使用 OnChildConfigured 初始化形状的属性  
 若要为第一个时，设置形状的属性创建、 重写`OnChildConfigured()`在关系图类的分部定义。 关系图类指定在 DSL 定义中，并且生成的代码位于**Dsl\Generated Code\Diagram.cs**。 例如：  
  
```c#  
partial class MyLanguageDiagram  
{  
  protected override void OnChildConfigured(ShapeElement child, bool childWasPlaced, bool createdDuringViewFixup)  
  {  
    base.OnChildConfigured(child, childWasPlaced, createdDuringViewFixup);  
    ExampleShape shape = child as ExampleShape;  
    if (shape != null)   
    {  
      if (!createdDuringViewFixup) return; // Ignore load from file.  
      ExampleElement element = shape.ModelElement as ExampleElement;  
      // Replace with a useful condition:  
      shape.FillColor = element.Name.EndsWith("3")   
          ? System.Drawing.Color.Red : System.Drawing.Color.Green;  
    }  
    // else deal with other types of shapes and connectors.  
  }  
}  
  
```  
  
 可以使用此方法，同时为域属性和非应用商店的功能，例如形状的大小。  
  
##  <a name="a-nameonassociatedpropertya-use-associatevaluewith-to-update-other-features-of-a-shape"></a><a name="OnAssociatedProperty"></a>使用 AssociateValueWith() 更新形状的其他功能  
 对于一个形状，例如是否具有阴影或连接线的箭头样式中的一些功能公开域属性的功能没有内置方法。  此类功能的更改不受控制的事务系统。 因此，不适合更新这些使用规则，因为当用户执行撤消命令不会调用规则。  
  
 相反，您可以通过使用<xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>。</xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>更新等功能 在下面的示例中，连接线的箭头样式控制的连接器显示关系中的域属性的值︰  
  
```  
public partial class ArrowConnector // My connector class.   
{  
   /// <summary>  
    /// Called whenever a registered property changes in the associated model element.  
    /// </summary>  
    /// <param name="e"></param>  
    protected override void OnAssociatedPropertyChanged(VisualStudio.Modeling.Diagrams.PropertyChangedEventArgs e)  
    {  
      base.OnAssociatedPropertyChanged(e);  
      // Can be called for any property change. Therefore,  
      // Verify that this is the property we're interested in:  
      if ("IsDirected".Equals(e.PropertyName))  
      {  
        if (e.NewValue.Equals(true))  
        { // Update the shape’s built-in Decorator feature:  
          this.DecoratorTo = LinkDecorator.DecoratorEmptyArrow;  
        }  
        else  
        {  
          this.DecoratorTo = null; // No arrowhead.  
        }  
      }  
    }  
    // OnAssociatedPropertyChanged is called only for properties  
    // that have been registered using AssociateValueWith().  
    // InitializeResources is a convenient place to call this.  
    // This method is invoked only once per class, even though  
    // it is an instance method.   
    protected override void InitializeResources(StyleSet classStyleSet)  
    {  
      base.InitializeResources(classStyleSet);  
      AssociateValueWith(this.Store, Wire.IsDirectedDomainPropertyId);  
      // Add other properties here.  
    }  
}  
  
```  
  
 `AssociateValueWith()`应调用一次每个你想要注册的域属性。 已调用后，将调用对指定的属性的任何更改`OnAssociatedPropertyChanged()`中存在该属性的模型元素的所有形状。  
  
 不需要调用`AssociateValueWith()`为每个实例。 虽然 InitializeResources 是实例方法，它被调用一次只能为每个形状类。

