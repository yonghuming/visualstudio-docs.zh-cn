---
title: "规则将在模型中的更改传播 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "域特定语言中，域模型进行编程"
  - "规则的域特定语言"
ms.assetid: 1690a38a-c8f5-4bc6-aab9-015771ec6647
caps.latest.revision: 30
caps.handback.revision: 30
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 规则将在模型中的更改传播
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以创建将更改传播从一个元素到另一个可视化和建模 SDK \(VMSDK\) 中的存储规则。 在存储区中的任何元素发生了更改，规则将计划时要执行，通常最外层的事务被提交。 有不同类型的不同种类的事件，如添加一个元素，或删除它的规则。 可以将规则附加到特定类型的元素、 形状或关系图。 许多内置功能由规则定义︰ 例如，规则可确保当在模型更改时，更新关系图。 可以添加您自己的规则来自定义您的域特定语言。  
  
 将内部存储区 – 也就是说，更改传播对更改的模型元素、 关系、 形状或连接符和他们的域属性，将规则保存程序特别有用。 当用户调用撤消或重做命令不运行规则。 相反，事务管理器可确保存储内容被还原到正确的状态。 如果您想要将更改传播到 store 外的资源，使用存储的事件。 有关详细信息，请参阅[事件处理程序在模型外部传播更改](../modeling/event-handlers-propagate-changes-outside-the-model.md)。  
  
 例如，假设您想要指定，只要用户 （或您的代码） 创建一个新元素的类型 ExampleDomainClass，则另一种类型的其他元素以另一个模型的一部分创建。 您可以编写 AddRule 并将其与 ExampleDomainClass 关联。 在要创建其他元素的规则，应编写的代码。  
  
```c#  
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
  
    // Code here propagates change as required – for example:  
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
>  规则的代码应更改仅的存储区; 中的元素的状态也就是说，该规则应更改仅模型元素、 关系、 形状、 连接符、 关系图或它们的属性。 如果您想要将更改传播到 store 外的资源，定义存储事件。 有关详细信息，请参阅[事件处理程序在模型外部传播更改](../modeling/event-handlers-propagate-changes-outside-the-model.md)。  
  
### 定义规则  
  
1.  定义规则，如类前加上 `RuleOn` 属性。 该属性将规则与其中一个域类、 关系或关系图元素相关联。 该规则将应用于此类，这可能是抽象的每个实例。  
  
2.  通过将其添加到所返回的集来注册该规则 `GetCustomDomainModelTypes()` 域模型类中。  
  
3.  规则类派生一个抽象的规则类，并编写执行方法的代码。  
  
 以下各节描述了更多详细介绍这些步骤。  
  
### 若要在域类上定义的规则  
  
-   在自定义代码文件中，定义一个类和它前面加 <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> 属性︰  
  
    ```  
    [RuleOn(typeof(ExampleElement),   
         // Usual value – but required, because it is not the default:  
         FireTime = TimeToFire.TopLevelCommit)]   
    class MyRule ...  
  
    ```  
  
-   中的第一个参数的使用者类型可以是域类、 域之间的关系、 形状、 连接符或关系图。 通常情况下，将规则应用于域类和关系。  
  
     `FireTime` 通常是 `TopLevelCommit`。 这可确保仅进行的事务的所有主要更改之后执行规则。 备选方法是内联，规则的执行长时间之后更改;和 LocalCommit，将在当前事务 （这可能不是最外面） 末尾的规则的执行。 您还可以设置会影响其在队列中，排序规则的优先级，但这是一种不可靠的方法来实现所需的结果。  
  
-   作为使用者类型，可以指定一个抽象类。  
  
-   此规则适用于使用者类的所有实例。  
  
-   默认值为 `FireTime` 是 TimeToFire.TopLevelCommit。 这会导致要外层事务提交时执行的规则。 一种替代方法是 TimeToFire.Inline。 这将导致在触发事件之后立即执行的规则。  
  
### 若要注册规则  
  
-   将规则的类添加到列表中返回的类型 `GetCustomDomainModelTypes` 域模型中︰  
  
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
  
-   如果您不确定您的域模型类的名称，查找文件内 **Dsl\\GeneratedCode\\DomainModel.cs**  
  
-   在 DSL 项目中的自定义代码文件中编写此代码。  
  
### 若要编写规则的代码  
  
-   从以下基类，这些类之一派生规则类︰  
  
    |基类|触发器|  
    |--------|---------|  
    |<xref:Microsoft.VisualStudio.Modeling.AddRule>|添加元素、 链接或形状。<br /><br /> 用于检测新关系，除了新元素。|  
    |<xref:Microsoft.VisualStudio.Modeling.ChangeRule>|更改域属性值。 该方法的参数提供的旧的和新值。<br /><br /> 对于形状，触发此规则时内置 `AbsoluteBounds` 属性更改，如果该形状移动。<br /><br /> 在许多情况下，它会重写更方便 `OnValueChanged` 或 `OnValueChanging` 属性处理程序中。 立即之前和之后更改调用这些方法。 与此相反，此规则通常运行在该事务的末尾。 有关详细信息，请参阅[域属性值更改处理程序](../modeling/domain-property-value-change-handlers.md)。 **Note:**  创建或删除链接时，则不会触发此规则。 相反，编写 `AddRule` 和 `DeleteRule` 域关系。|  
    |<xref:Microsoft.VisualStudio.Modeling.DeletingRule>|当某个元素或链接是将要删除时触发。 该属性 ModelElement.IsDeleting 事务结束时才为 true。|  
    |<xref:Microsoft.VisualStudio.Modeling.DeleteRule>|在元素或链接已被删除时执行。 已执行的所有其他规则，包括 DeletingRules 后执行规则。 ModelElement.IsDeleting 为 false，且 ModelElement.IsDeleted 为 true。 若要允许随后的撤消，该元素并不实际删除从内存中，但从 Store.ElementDirectory 中删除。|  
    |<xref:Microsoft.VisualStudio.Modeling.MoveRule>|元素是将从一个存储分区移到另一个。<br /><br /> （请注意这不相关的图形形状的位置）。|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>|此规则仅适用于域关系。 如果显式将模型元素分配给任一端的链接，它将触发。|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule>|当链接指向或来自元素的顺序在链路上使用 MoveBefore 或 MoveToIndex 方法发生更改时触发。|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>|创建一个事务时执行。|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>|大约要提交事务时执行。|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>|要回滚事务时执行。|  
  
-   每个类有一个您重写的方法。 类型 `override` 在类中发现它。 此方法的参数标识要更改的元素。  
  
 请注意关于规则的以下几点︰  
  
1.  组在事务中的更改可能会触发多个规则。 通常情况下，提交外部事务时，会执行规则。 将按未指定的顺序执行它们。  
  
2.  一条规则始终在事务内执行。 因此，不需要创建一个新事务来进行更改。  
  
3.  事务回滚时，或执行撤消或重做操作时，不会执行规则。 这些操作将存储的所有内容重都置为其以前的状态。 因此，如果您的规则在存储外的任何对象的状态更改时，它可能会将保留在与应用商店 synchronism 内容。 若要更新在存储外的状态，则最好使用事件。 有关更多信息，请参见[事件处理程序在模型外部传播更改](../modeling/event-handlers-propagate-changes-outside-the-model.md)。  
  
4.  从文件加载模型时，将执行一些规则。 若要确定是否加载或保存正在进行，请使用 `store.TransactionManager.CurrentTransaction.IsSerializing`。  
  
5.  如果您的规则的代码创建多个规则触发器，它们将被添加到列表末尾的激发，并在事务完成之前将执行。 DeletedRules 筛选器之后执行的所有其他规则。 一条规则可以在事务中，针对每项更改一次运行多次。  
  
6.  要传递到和从规则的信息，可以将存储中的信息 `TransactionContext`。 这是只是一个字典，其中在事务处理期间维护。 事务结束时释放它。 每个规则中的事件参数提供给它的访问。 请记住可预知的顺序中的用户不能执行规则。  
  
7.  在考虑其他备选方案后的使用规则。 例如，如果您想要更新属性值更改时，请考虑使用计算的属性。 如果您想要限制的大小或形状的位置，使用 `BoundsRule`。 如果您想要对属性值的更改作出响应，将添加 `OnValueChanged` 给属性的处理程序。 有关更多信息，请参见[响应并传播更改](../modeling/responding-to-and-propagating-changes.md)。  
  
## 示例  
 域关系进行实例化，若要链接两个元素时，下面的示例将更新属性。 不仅在用户上创建一个链接关系图中，而且如果程序代码将创建一个链接时，将会触发此规则。  
  
 若要测试此示例中，创建 DSL 使用任务流解决方案模板，并在 Dsl 项目中的文件中插入下面的代码。 生成和运行解决方案，并打开调试项目中的示例文件。 注释形状和数据流元素之间绘制注释链接。 注释中的文本更改为已连接到的最新元素上的报表。  
  
 在实践中，您通常会为每个 AddRule 编写 DeleteRule。  
  
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
  
## 请参阅  
 [事件处理程序在模型外部传播更改](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [BoundsRules 约束形状位置和大小](../modeling/boundsrules-constrain-shape-location-and-size.md)