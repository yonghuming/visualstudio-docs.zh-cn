---
title: "更新形状和连接符以反映模型 |Microsoft 文档"
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: ae3a0d952b8ff88f2df4d297509d01d1a6731d56
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="updating-shapes-and-connectors-to-reflect-the-model"></a>更新形状和连接线以反映模型
域特定语言中[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，你可以反映的基础模型的状态的形状的外观。  
  
 本主题中的代码示例应添加到`.cs`文件在你`Dsl`项目。 你将需要每个文件中的这些语句：  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  
```  
  
## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>设置形状地图属性以控制可见性修饰器  
 你可以控制的可见性修饰器，而无需编写程序代码中，通过配置 DSL 定义中的形状和域类之间的映射。 有关详细信息，请参阅[如何定义域特定语言](../modeling/how-to-define-a-domain-specific-language.md)。
  
## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>将作为属性公开的颜色和样式的形状  
 在 DSL 定义中，右击形状类，指向**添加公开**，然后单击某一项如**填充颜色**。  
  
 形状现在具有一个域属性，你可以在程序代码中或作为用户设置。 例如，若要在命令或规则的程序代码中设置它，你可以编写：  
  
 `shape.FillColor = System.Drawing.Color.Red;`  
  
 如果你想要使属性变量，仅在程序控制，而不是用户，选择新的域属性，如**填充颜色**DSL 定义关系图中。 然后，在属性窗口中，设置**是可浏览**到`false`或设置**是 UI Readonly**到`true`。  
  
## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>定义更改规则，可以使颜色、 样式或依赖于模型元素属性的位置  
 你可以定义更新依赖于模型的其他部分的形状的外观的规则。 例如，你可以更改规则定义更新其依赖于模型元素的属性的形状的颜色的模型元素。 有关更改规则的详细信息，请参阅[规则传播更改内模型](../modeling/rules-propagate-changes-within-the-model.md)。  
  
 应使用规则仅用于更新内应用商店中，保留的属性，因为规则不会在执行撤销命令时调用。 这不包括一些图形功能，例如大小和形状的可见性。 若要更新的一种形状的这些功能，请参阅[更新非存储图形功能](#OnAssociatedProperty)。  
  
 下面的示例假定你具有公开`FillColor`作为域属性上一节中所述。  
  
```csharp  
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
 若要设置形状的属性，第一个时创建，重写`OnChildConfigured()`图类的分部定义中。 关系图类指定在 DSL 定义中，并且生成的代码是在**Dsl\Generated Code\Diagram.cs**。 例如:   
  
```csharp  
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
  
 域属性和非应用商店功能，例如形状的大小，则可以使用此方法。  
  
##  <a name="OnAssociatedProperty"></a>使用 AssociateValueWith() 更新形状的其他功能  
 对于一个形状上，例如是否具有阴影或连接器的箭头样式的某些功能公开域属性的功能没有内置方法。  此类功能的更改不受控制的事务系统中。 因此，不合适更新它们使用规则，因为用户执行撤销命令时，不会调用规则。  
  
 相反，您可以通过使用更新此类功能<xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>。 在下面的示例中，连接器的箭头样式控制的连接器显示的关系中的域属性值：  
  
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
        { // Update the shape's built-in Decorator feature:  
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
  
 `AssociateValueWith()`应调用一次为每个你想要注册的域属性。 已调用后，将调用对指定的属性的任何更改`OnAssociatedPropertyChanged()`中存在该属性的模型元素的任何形状。  
  
 不需要调用`AssociateValueWith()`每个实例。 尽管 InitializeResources 是实例方法，它被调用一次只能为每个形状类。

