---
title: "规则将在模型内的更改传播 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
ms.assetid: 1690a38a-c8f5-4bc6-aab9-015771ec6647
caps.latest.revision: "30"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 8ec9540fb68ecb09dc592f9b05a56291c2a8c80d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="rules-propagate-changes-within-the-model"></a>规则在模型内部传播更改
你可以创建应用商店规则传播到另一个中可视化和建模 SDK (VMSDK) 从在元素更改。 时对存储区中任何元素发生了更改，规则都计划在最外层事务提交时通常要执行。 有不同类型的不同种类的事件，如添加元素，或删除它的规则。 你可以附加到特定类型的元素、 形状或关系图的规则。 许多内置功能由规则定义： 例如，规则确保在模型更改时，更新关系图。 你可以通过添加您自己的规则自定义你的域特定语言。  
  
 将内部存储区-即，更改传播更改到模型元素、 关系、 形状或连接器和其域属性，应用商店规则是特别有用。 规则不运行时，用户调用撤消或重做命令。 相反，事务管理器可确保应用商店内容已还原到正确的状态。 如果你想要将更改传播到外部存储资源，使用存储的事件。 有关详细信息，请参阅[事件处理程序传播更改外部模型](../modeling/event-handlers-propagate-changes-outside-the-model.md)。  
  
 例如，假设你想要指定每当用户 （或你的代码） 创建一个新元素的类型 ExampleDomainClass，另一种类型的其他元素在模型的另一部分中进行创建。 无法写入 AddRule 并将其与 ExampleDomainClass 关联。 规则创建的其他元素中，你将编写代码。  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
  
namespace ExampleNamespace  
{  
 // Attribute associates the rule with a domain class:  
 [RuleOn(typeof(ExampleDomainClass), FireTime=TimeToFire.TopLevelCommit)]  
 // The rule is a class derived from one of the abstract rules:  
 class MyAddRule : AddRule  
 {  
  // Override the abstract method:  
  public override void ElementAdded(ElementAddedEventArgs e)  
  {  
    base.ElementAdded(e);  
    ExampleDomainClass element = e.ModelElement;  
    Store store = element.Store;  
    // Ignore this call if we're currently loading a model:  
    if (store.TransactionManager.CurrentTransaction.IsSerializing)   
       return;  
  
    // Code here propagates change as required - for example:  
      AnotherDomainClass echo = new AnotherDomainClass(element.Partition);  
      echo.Name = element.Name;  
      echo.Parent = element.Parent;    
    }  
  }  
 // The rule must be registered:  
 public partial class ExampleDomainModel  
 {  
   protected override Type[] GetCustomDomainModelTypes()  
   {  
     List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
     types.Add(typeof(MyAddRule));  
     // If you add more rules, list them here.   
     return types.ToArray();  
   }  
 }  
}  
  
```  
  
> [!NOTE]
>  规则的代码应更改仅存储区; 中的元素的状态也就是说，该规则应更改仅模型元素、 关系、 形状、 连接器、 关系图或其属性。 如果你想要将更改传播到外部存储资源，定义存储事件。 有关详细信息，请参阅[事件处理程序传播更改外部模型](../modeling/event-handlers-propagate-changes-outside-the-model.md)  
  
### <a name="to-define-a-rule"></a>定义规则  
  
1.  定义规则，如类前加`RuleOn`属性。 该属性将与你的域类、 关系或关系图元素之一关联规则。 规则将应用于此类，这可能是抽象的每个实例。  
  
2.  通过将它添加到返回的集中注册规则`GetCustomDomainModelTypes()`域模型类中。  
  
3.  规则类派生的一个抽象的规则类，并且编写执行方法的代码。  
  
 以下各节描述了详细介绍这些步骤。  
  
### <a name="to-define-a-rule-on-a-domain-class"></a>若要域类上定义规则  
  
-   在自定义代码文件中，定义的类和它前面加<xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute>属性：  
  
    ```  
    [RuleOn(typeof(ExampleElement),   
         // Usual value - but required, because it is not the default:  
         FireTime = TimeToFire.TopLevelCommit)]   
    class MyRule ...  
  
    ```  
  
-   中的第一个参数的使用者类型可以是域类、 域关系、 形状、 连接器或关系图。 通常情况下，将规则应用于域类和关系。  
  
     `FireTime`通常是`TopLevelCommit`。 这可确保仅在进行的事务的所有主更改之后执行规则。 替代项为内联，更改; 之后立即执行规则和 LocalCommit，执行在当前事务 （这可能不是最外层） 末尾规则。 你还可以设置会影响在队列中，其排序规则的优先级，但这是一个不可靠的方法的实现需要的结果。  
  
-   你可以指定一个抽象类作为使用者类型。  
  
-   该规则适用于使用者类的所有实例。  
  
-   默认值为`FireTime`是 TimeToFire.TopLevelCommit。 这将导致在最外层事务提交时执行的规则。 一种替代方法是 TimeToFire.Inline。 这将导致触发的事件之后立即执行的规则。  
  
### <a name="to-register-the-rule"></a>注册规则  
  
-   将规则的类添加到返回的类型列表`GetCustomDomainModelTypes`域模型中：  
  
    ```  
    public partial class ExampleDomainModel  
     {  
       protected override Type[] GetCustomDomainModelTypes()  
       {  
         List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
         types.Add(typeof(MyAddRule));  
         // If you add more rules, list them here.   
         return types.ToArray();  
       }  
     }  
  
    ```  
  
-   如果你不确定你的域模型类的名称，查找文件内**Dsl\GeneratedCode\DomainModel.cs**  
  
-   DSL 项目中的自定义代码文件中编写此代码。  
  
### <a name="to-write-the-code-of-the-rule"></a>若要编写的代码的规则  
  
-   从以下基类，这些类之一派生规则类：  
  
    |基类|触发器|  
    |----------------|-------------|  
    |<xref:Microsoft.VisualStudio.Modeling.AddRule>|添加元素、 链接或在形状。<br /><br /> 用于检测新关系，除了新元素。|  
    |<xref:Microsoft.VisualStudio.Modeling.ChangeRule>|更改域属性值。 方法自变量提供的旧和新值。<br /><br /> 对于形状，触发此规则时内置`AbsoluteBounds`属性更改，如果移动形状。<br /><br /> 在许多情况下，它是更方便地重写`OnValueChanged`或`OnValueChanging`属性处理程序中。 更改立即之前和之后调用这些方法。 与此相反，此规则通常运行在事务的末尾。 有关详细信息，请参阅[域属性值更改处理程序](../modeling/domain-property-value-change-handlers.md)。 **注意：**创建或删除链接时，则不触发此规则。 相反，编写`AddRule`和`DeleteRule`域关系。|  
    |<xref:Microsoft.VisualStudio.Modeling.DeletingRule>|当某个元素或链接是即将被删除时触发。 在事务结束之前，属性 ModelElement.IsDeleting 为 true。|  
    |<xref:Microsoft.VisualStudio.Modeling.DeleteRule>|执行时已删除的元素或链接。 所有其他规则具有执行，包括 DeletingRules 后执行规则。 ModelElement.IsDeleting 为 false，并且 ModelElement.IsDeleted 为 true。 若要允许后续撤消，元素不实际从内存中删除，但从 Store.ElementDirectory 中删除。|  
    |<xref:Microsoft.VisualStudio.Modeling.MoveRule>|元素从一个存储区分区移动到另一个。<br /><br /> （请注意这不相关的图形的位置确定的一种形状。）|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>|此规则仅适用于域关系。 如果你显式将模型元素分配给链接的任意一端，触发它时。|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule>|链接到或从某个元素的顺序链接上使用的 MoveBefore 或 MoveToIndex 方法更改时触发。|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>|在创建事务时执行。|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>|事务将被提交时执行。|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>|执行事务时将被回滚。|  
  
-   每个类具有您重写的方法。 类型`override`中你的类以发现它。 此方法的参数标识正在更改的元素。  
  
 请注意有关规则的以下几点：  
  
1.  在事务中的更改集可能会触发多规则。 通常情况下，外层事务已提交时，会执行规则。 它们将在未指定的顺序执行。  
  
2.  始终在事务内执行一条规则。 因此，无需创建新事务来进行更改。  
  
3.  事务回滚时，或执行撤消或重做操作时，不会执行规则。 这些操作重置为其以前状态的应用商店中的所有内容。 因此，如果你的规则发生更改的存储区之外的任何内容的状态，也可能不保留在与应用商店的 synchronism 内容。 若要更新 Store 外的状态，则最好使用事件。 有关详细信息，请参阅[事件处理程序传播更改外部模型](../modeling/event-handlers-propagate-changes-outside-the-model.md)。  
  
4.  从文件加载模型时，将执行一些规则。 若要确定是否加载或保存正在进行，请使用`store.TransactionManager.CurrentTransaction.IsSerializing`。  
  
5.  如果你的规则的代码将创建多个规则将触发，它们将添加到列表末尾的触发，并在事务完成之前将执行。 在所有其他规则之后执行 DeletedRules。 一个规则可以在事务中，针对每项更改一次运行多次。  
  
6.  要传递信息与其他规则，你可以将信息存储在`TransactionContext`。 这是仅一个字典，其中在事务处理期间保留。 事务结束时释放它。 每个规则中的事件自变量提供对它的访问。 请记住可预测的顺序的用户不能执行规则。  
  
7.  考虑其他备选方案后的使用规则。 例如，如果你想要更新属性值更改时，请考虑使用计算的属性。 如果你想要限制的大小或位置的形状，使用`BoundsRule`。 如果你想要对的属性值更改做出响应，将添加`OnValueChanged`给属性的处理程序。 有关详细信息，请参阅[响应和传播更改](../modeling/responding-to-and-propagating-changes.md)。  
  
## <a name="example"></a>示例  
 在实例化的域关系链接两个元素时，下面的示例将更新属性。 不仅在用户上创建一个链接一个关系图，但还如果程序代码会创建一个链接，将触发该规则。  
  
 若要测试此示例，请创建 DSL 使用任务流解决方案模板，并在 Dsl 项目中的文件中插入以下代码。 生成和运行解决方案，并在调试项目中打开示例文件。 绘制注释形状和数据流元素之间的注释链接。 注释中的文本更改为你已连接到的最新元素上的报表。  
  
 在实践中，你通常将为每个 AddRule 编写 DeleteRule。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Microsoft.VisualStudio.Modeling;  
  
namespace Company.TaskRuleExample  
{  
  
  [RuleOn(typeof(CommentReferencesSubjects))]  
  public class RoleRule : AddRule  
  {  
  
    public override void ElementAdded(ElementAddedEventArgs e)  
    {  
      base.ElementAdded(e);  
      CommentReferencesSubjects link = e.ModelElement as CommentReferencesSubjects;  
      Comment comment = link.Comment;  
      FlowElement subject = link.Subject;  
      Transaction current = link.Store.TransactionManager.CurrentTransaction;  
      // Don't want to run when we're just loading from file:  
      if (current.IsSerializing) return;  
      comment.Text = "Flow has " + subject.FlowTo.Count + " outgoing connections";  
    }  
  
  }  
  
  public partial class TaskRuleExampleDomainModel  
  {  
    protected override Type[] GetCustomDomainModelTypes()  
    {  
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
      types.Add(typeof(RoleRule));  
      return types.ToArray();  
    }  
  }  
  
}  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [事件处理程序将在模型外部更改传播](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [BoundsRules 约束形状位置和大小](../modeling/boundsrules-constrain-shape-location-and-size.md)