---
title: "导航和更新中的模型程序代码 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, programming domain models
ms.assetid: 1427ae91-be8a-4ce7-85df-00038faa2cbb
caps.latest.revision: "26"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 5c7571cbb4950f91c1b69ae88241c799577f79da
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="navigating-and-updating-a-model-in-program-code"></a>在程序代码中导航和更新模型
你可以编写代码以创建和删除模型元素、 设置其属性，并创建和删除元素之间的链接。 必须在事务中进行所有更改。 如果元素在关系图上查看，关系图将""自动更正事务的末尾。  
  
## <a name="in-this-topic"></a>本主题内容  
 [DSL 定义示例](#example)  
  
 [导航模型](#navigation)  
  
 [访问类信息](#metadata)  
  
 [执行在事务内的更改](#transaction)  
  
 [创建模型元素](#elements)  
  
 [创建关系链接](#links)  
  
 [删除元素](#deleteelements)  
  
 [删除关系链接](#deletelinks)  
  
 [重新排序的一种关系的链接](#reorder)  
  
 [锁](#locks)  
  
 [复制和粘贴](#copy)  
  
 [导航和更新关系图](#diagrams)  
  
 [形状和元素之间导航](#views)  
  
 [形状和连接器的属性](#shapeProperties)  
  
 [DocView 和 DocData](#docdata)  
  
##  <a name="example"></a>DSL 定义示例  
 这是本主题中的示例 DslDefinition.dsl 的主要部分：  
  
 ![DSL 定义关系图 &#45;王朝家谱模型](../modeling/media/familyt_person.png "FamilyT_Person")  
  
 此模型是此 DSL 的实例：  
  
 ![都铎王朝家谱模型](../modeling/media/tudor_familytreemodel.png "Tudor_FamilyTreeModel")  
  
### <a name="references-and-namespaces"></a>引用和命名空间  
 若要运行本主题中的代码，您应引用：  
  
 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`  
  
 你的代码将使用此命名空间：  
  
 `using Microsoft.VisualStudio.Modeling;`  
  
 此外，如果你正在从在其中定义 DSL 的不同项目中编写代码，则应导入由 Dsl 项目生成的程序集。  
  
##  <a name="navigation"></a>导航模型  
  
### <a name="properties"></a>属性  
 DSL 定义中定义的域属性变为可以访问在程序代码中的属性：  
  
 `Person henry = ...;`  
  
 `if (henry.BirthDate < 1500) ...`  
  
 `if (henry.Name.EndsWith("VIII")) ...`  
  
 如果你想要设置的属性，则必须执行这样内[事务](#transaction):  
  
 `henry.Name = "Henry VIII";`  
  
 如果在 DSL 定义中，一个属性的**类型**是**计算**，能将其设置。 有关详细信息，请参阅[计算和自定义存储属性](../modeling/calculated-and-custom-storage-properties.md)。  
  
### <a name="relationships"></a>关系  
 DSL 定义中定义的域关系会变得对属性，一个在两端的关系类。 属性的名称在 DslDefinition 关系图中显示为在每个关系的一端的角色上的标签。 具体取决于角色的重数，属性的类型是在另一端的关系类，或者此类的集合。  
  
 `foreach (Person child in henry.Children) { ... }`  
  
 `FamilyTreeModel ftree = henry.FamilyTreeModel;`  
  
 位于关系的相反端的属性始终是倒数。 创建或删除链接后，将更新这两个元素上的角色属性。 下面的表达式 (它使用的扩展`System.Linq`) 始终适用于在示例中的 ParentsHaveChildren 关系：  
  
 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`  
  
 `&& p.Parents.All(parent => parent.Children.Contains(p));`  
  
 **ElementLinks**。 关系也可由一个名为模型元素*链接*，这是域关系类型的实例。 链接始终具有一个源元素和一个目标元素。 源元素和目标元素可以是相同的。  
  
 你可以访问链接和其属性：  
  
 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`  
  
 `// This is now true:`  
  
 `link == null || link.Parent == henry && link.Child == edward`  
  
 默认情况下，不能超过一个实例的关系会允许链接模型元素的任何对。 但如果在 DSL 定义中，`Allow Duplicates`标志为 true 对于关系，则可能有多个链接，并且你必须使用`GetLinks`:  
  
 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`  
  
 还有其他一些方法用于访问链接。 例如:   
  
 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`  
  
 **隐藏的角色。** 如果在 DSL 定义中，**属性生成**是**false**对于特定角色，则没有属性会生成对应于该角色。 但是，你仍可以访问链接和遍历使用关系的方法的链接：  
  
 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`  
  
 最常使用的示例是<xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>关系，模型元素链接到显示在关系图的形状：  
  
 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`  
  
### <a name="the-element-directory"></a>元素目录  
 你可以访问存储区中使用的元素目录中的所有元素：  
  
 `store.ElementDirectory.AllElements`  
  
 也有一些方法，用于查找元素，如下所示：  
  
 `store.ElementDirectory.FindElements(Person.DomainClassId);`  
  
 `store.ElementDirectory.GetElement(elementId);`  
  
##  <a name="metadata"></a>访问类信息  
 你可以获取有关类、 关系和 DSL 定义的其他方面的信息。 例如:   
  
 `DomainClassInfo personClass = henry.GetDomainClass();`  
  
 `DomainPropertyInfo birthProperty =`  
  
 `personClass.FindDomainProperty("BirthDate")`  
  
 `DomainRelationshipInfo relationship =`  
  
 `link.GetDomainRelationship();`  
  
 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`  
  
 模型元素的上级类如下所示：  
  
-   模型元素的所有元素和关系是数目  
  
-   元角色的所有关系都是 ElementLinks  
  
##  <a name="transaction"></a>执行在事务内的更改  
 当你的程序代码发生更改存储区中的任何内容时，它必须在事务内将这样做。 这适用于所有模型元素、 关系、 形状、 关系图和其属性。 有关更多信息，请参见<xref:Microsoft.VisualStudio.Modeling.Transaction>。  
  
 管理事务的最方便的方法是借助`using`语句括在`try...catch`语句：  
  
```  
Store store; ...  
try  
{  
  using (Transaction transaction =  
    store.TransactionManager.BeginTransaction("update model"))  
    // Outermost transaction must always have a name.  
  {  
    // Make several changes in Store:  
    Person p = new Person(store);  
    p.FamilyTreeModel = familyTree;  
    p.Name = "Edward VI";  
    // end of changes to Store  
  
    transaction.Commit(); // Don't forget this!  
  } // transaction disposed here  
}  
catch (Exception ex)  
{  
  // If an exception occurs, the Store will be   
  // rolled back to its previous state.  
}  
```  
  
 你可以在一个事务内的更改的任何数。 你可以打开在活动事务内的新事务。  
  
 若要使所做的更改为永久更改，你应`Commit`事务之前已释放。 如果异常发生在事务捕获不到，存储将重置为其状态之前所做的更改。  
  
##  <a name="elements"></a>创建模型元素  
 此示例将元素添加到现有模型：  
  
```  
FamilyTreeModel familyTree = ...; // The root of the model.         
using (Transaction t =  
    familyTree.Store.TransactionManager  
    .BeginTransaction("update model"))  
{  
  // Create a new model element   
  // in the same partition as the model root:  
  Person edward = new Person(familyTree.Partition);  
  // Set its embedding relationship:  
  edward.FamilyTreeModel = familyTree;  
          // same as: familyTree.People.Add(edward);  
  // Set its properties:  
  edward.Name = "Edward VII";  
  t.Commit(); // Don't forget this!  
}  
```  
  
 此示例阐释了这些要点有关创建的元素：  
  
-   在特定分区的存储区中创建新的元素。 模型元素和关系，但不形状，这通常是默认分区。  
  
-   请将它嵌入关系的目标。 在此示例 DslDefinition，每个人员必须嵌入关系 FamilyTreeHasPeople 的目标。 若要实现此目的，我们可以设置 FamilyTreeModel 角色属性的 Person 对象，或将用户添加到 FamilyTreeModel 对象的用户角色属性。  
  
-   设置的新元素，尤其是为其属性的属性`IsName`DslDefinition 中是如此。 此标志将标记来标识唯一内其所有者的元素的属性。 在这种情况下，该名称属性具有该标志。  
  
-   到存储中，必须已加载此 DSL 的 DSL 定义。 如果你正在编写如菜单命令的扩展，这通常会已 true。 在其他情况下，你可以显式将模型加载到应用商店，或者使用<xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus>加载它。 有关详细信息，请参阅[如何： 从在程序代码中的文件打开模型](../modeling/how-to-open-a-model-from-file-in-program-code.md)。  
  
 当以这种方式创建一个元素时，（如果 DSL 具有关系图），将自动创建一种形状。 它显示在自动分配的位置中，使用默认形状、 颜色和其他功能。 如果你想要控制在何处以及如何显示相关联的形状，请参阅[创建元素和其形状](#merge)。  
  
##  <a name="links"></a>创建关系链接  
 有两个示例 DSL 定义中定义的关系。 每个关系定义*角色属性*两端的关系类。  
  
 有三种方法可以在其中创建关系的实例。 这三种方法的每个具有相同的效果：  
  
-   设置的属性的源角色扮演者。 例如:   
  
    -   `familyTree.People.Add(edward);`  
  
    -   `edward.Parents.Add(henry);`  
  
-   将目标角色扮演者属性设置。 例如:   
  
    -   `edward.familyTreeModel = familyTree;`  
  
         此角色的重数是`1..1`，因此我们将值分配。  
  
    -   `henry.Children.Add(edward);`  
  
         此角色的重数是`0..*`，因此我们将添加到集合。  
  
-   显式构造关系的实例。 例如:   
  
    -   `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`  
  
    -   `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`  
  
 最后一个方法是很有用，如果你想要在关系本身上设置属性。  
  
 当以这种方式创建一个元素时，自动创建关系图上的连接器，但它具有默认形状、 颜色和其他功能。 若要控制如何创建关联的连接器，请参阅[创建元素和其形状](#merge)。  
  
##  <a name="deleteelements"></a>删除元素  
 通过调用中删除某个元素`Delete()`:  
  
 `henry.Delete();`  
  
 此操作还将删除：  
  
-   关系链接到和从元素。 例如，`edward.Parents`将不再包含`henry`。  
  
-   元素出现在为其角色`PropagatesDelete`标志为 true。 例如，将删除显示元素的形状。  
  
 默认情况下，每个嵌入关系具有`PropagatesDelete`true 在目标的角色。 删除`henry`不会删除`familyTree`，但`familyTree.Delete()`将删除所有`Persons`。 有关详细信息，请参阅[自定义删除行为](../modeling/customizing-deletion-behavior.md)。  
  
 默认情况下，`PropagatesDelete`不适用于引用关系的角色。  
  
 你可能会导致删除规则，以忽略特定传播时删除对象。 这是如果你一个元素替换为另一个有用的。 提供为其不应传播删除的一个或多个角色的 GUID。 可以从关系类获取 GUID:  
  
 `henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`  
  
 (此特定示例将不起作用，因为`PropagatesDelete`是`false`的角色`ParentsHaveChildren`关系。)  
  
 在某些情况下，删除将阻止的锁，元素上或在传播将删除的元素上存在。 你可以使用`element.CanDelete()`以检查是否可以删除元素。  
  
##  <a name="deletelinks"></a>删除关系链接  
 你可以通过从角色属性中移除元素中删除的关系链接：  
  
 `henry.Children.Remove(edward); // or:`  
  
 `edward.Parents.Remove(henry);  // or:`  
  
 你可以显式删除的链接：  
  
 `edwardHenryLink.Delete();`  
  
 所有这三种方法具有相同的效果。 只需使用其中一个。  
  
 如果角色的 0..1 或 1..1 重数，可以将其设置为`null`，或为其他值：  
  
 `edward.FamilyTreeModel = null;`或：  
  
 `edward.FamilyTreeModel = anotherFamilyTree;`  
  
##  <a name="reorder"></a>重新排序的一种关系的链接  
 源或目标特定的模型元素的一特定关系的链接有特定的顺序。 它们显示在已添加的顺序。 例如，此语句将始终产生相同顺序的子级：  
  
 `foreach (Person child in henry.Children) ...`  
  
 你可以更改的链接顺序：  
  
 `ParentsHaveChildren link = GetLink(henry,edward);`  
  
 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`  
  
 `DomainRoleInfo role =`  
  
 `link.GetDomainRelationship().DomainRoles[0];`  
  
 `link.MoveBefore(role, nextLink);`  
  
##  <a name="locks"></a>锁  
 所做的更改可能会阻止的锁。 可以设置锁，各个元素、 分区和存储。 如果任何这些级别必须锁来防止你想要的更改的类型，当你尝试时可能引发异常。 你可以发现是否锁使用设置的元素。GetLocks()，命名空间中定义的扩展方法<xref:Microsoft.VisualStudio.Modeling.Immutability>。  
  
 有关详细信息，请参阅[创建只读线段定义锁定策略](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)。  
  
##  <a name="copy"></a>复制和粘贴  
 你可以复制元素或元素组<xref:System.Windows.Forms.IDataObject>:  
  
```  
Person person = personShape.ModelElement as Person;  
Person adopter = adopterShape.ModelElement as Person;  
IDataObject data = new DataObject();  
personShape.Diagram.ElementOperations  
      .Copy(data, person.Children.ToList<ModelElement>());  
```  
  
 元素的序列化的元素组作为存储。  
  
 可以将从 IDataObject 元素合并到一个模型：  
  
```  
using (Transaction t = targetDiagram.Store.  
        TransactionManager.BeginTransaction("paste"))  
{  
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);  
}  
```  
  
 `Merge ()`可以接受`PresentationElement`或`ModelElement`。 如果你赋予它`PresentationElement`，也可以作为第三个参数的目标关系图上指定的位置。  
  
##  <a name="diagrams"></a>导航和更新关系图  
 DSL，在域模型元素，它表示如人员或歌曲的概念，是独立于形状元素，它表示关系图上看到的内容。 域模型元素存储的重要属性和关系的概念。 形状元素存储大小、 位置和颜色的关系图的对象的视图和其组成部分的布局。  
  
### <a name="presentation-elements"></a>表示元素  
 ![基本形状和元素类型的类图](../modeling/media/dslshapesandelements.png "DSLshapesAndElements")  
  
 在你的 DSL 定义，你指定每个元素创建从以下标准类之一派生的类。  
  
|一种元素|基类|  
|---------------------|----------------|  
|域类|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|  
|域关系|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|  
|形状|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|  
|连接符|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|  
|关系图|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|  
  
 关系图上的元素通常表示的模型元素。 通常 （但不是总是），<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>表示域类实例和一个<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>表示域关系实例。 <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>关系节点或链接将形状链接到它所表示的模型元素。  
  
 每个节点或链接形状属于一个关系图。 二进制链接形状连接两个节点形状。  
  
 形状可以有两个集的子形状。 中的一个形状`NestedChildShapes`集限制为其父级的边界框。 中的一个形状`RelativeChildShapes`列表可以显示外侧或部分父-例如标签或端口范围之外。 关系图没有`RelativeChildShapes`并且不`Parent`。  
  
###  <a name="views"></a>形状和元素之间导航  
 通过相关域的模型元素和形状元素<xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>关系。  
  
```csharp  
// using Microsoft.VisualStudio.Modeling;  
// using Microsoft.VisualStudio.Modeling.Diagrams;  
// using System.Linq;  
Person henry = ...;  
PersonShape henryShape =   
  PresentationViewsSubject.GetPresentation(henry)  
    .FirstOrDefault() as PersonShape;  
```  
  
 同一关系链接到关系图上的连接器的关系：  
  
```  
Descendants link = Descendants.GetLink(henry, edward);  
DescendantConnector dc =  
   PresentationViewsSubject.GetPresentation(link)  
     .FirstOrDefault() as DescendantConnector;  
// dc.FromShape == henryShape && dc.ToShape == edwardShape  
```  
  
 此关系还链接到关系图的模型的根：  
  
```  
FamilyTreeDiagram diagram =   
   PresentationViewsSubject.GetPresentation(familyTree)  
      .FirstOrDefault() as FamilyTreeDiagram;  
```  
  
 若要获取形状所表示的模型元素，请使用：  
  
 `henryShape.ModelElement as Person`  
  
 `diagram.ModelElement as FamilyTreeModel`  
  
### <a name="navigating-around-the-diagram"></a>导航关系图  
 一般情况下不建议形状和关系图上的连接器间导航。 它是更好的做法导航的关系在模型中，必要的关系图的外观上工作时之间的形状和连接符移动。 这些方法将连接器链接到每一端形状：  
  
 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`  
  
 `connector.FromShape, connector.ToShape`  
  
 多个形状是复合服务;它们的父形状和的子级的一个或多个层组成。 位于相对于另一种形状的形状可认为是其*子级*。 当父形状移动时，子项将随之移动。  
  
 *相对子级*可以显示父形状的边界框外部。 *嵌套*子级显示严格父边界内。  
  
 若要获取的关系图上形状顶部的一组，请使用：  
  
 `Diagram.NestedChildShapes`  
  
 形状和连接符的上级类如下：  
  
 <xref:Microsoft.VisualStudio.Modeling.ModelElement>  
  
 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>  
  
 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>  
  
 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>  
  
 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>  
  
 ------- *YourShape*  
  
 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>  
  
 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>  
  
 --------- *YourConnector*  
  
###  <a name="shapeProperties"></a>形状和连接器的属性  
 在大多数情况下，不需要对形状进行显式更改。 当你更改的模型元素时，"修复"规则更新形状和连接符。 有关详细信息，请参阅[响应和传播更改](../modeling/responding-to-and-propagating-changes.md)。  
  
 但是，它可用于独立于的模型元素的属性中的形状做一些显式更改。 例如，你无法更改这些属性：  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A>-确定的高度和宽度的形状。  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A>-位置相对于父形状或关系图  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A>-钢笔和画笔用于绘制形状或连接器的集  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A>-使形状不可见  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A>-使形状后可见`Hide()`  
  
###  <a name="merge"></a>创建元素和其形状  
 当你创建一个元素，并将其链接到嵌入关系的树时，形状上自动创建并与之关联。 这可通过在事务结束执行的"修正"规则。 但是，形状将显示在自动分配的位置，并且其形状、 颜色和其他功能将具有默认值。 若要控制如何创建形状，可以使用合并功能。 必须先添加你想要添加到 ElementGroup 的元素，然后将组合并到关系图。  
  
 此方法：  
  
-   如果你已分配为元素名称的属性的名称，请将其设置。  
  
-   观察 DSL 定义中指定任何元素合并指令。  
  
 此示例创建一个形状鼠标位置中，当用户双击关系图。 在此示例中，DSL 定义`FillColor`属性`ExampleShape`已公开。  
  
```  
  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
partial class MyDiagram  
{  
  public override void OnDoubleClick(DiagramPointEventArgs e)  
  {  
    base.OnDoubleClick(e);  
  
    using (Transaction t = this.Store.TransactionManager  
        .BeginTransaction("double click"))  
    {  
      ExampleElement element = new ExampleElement(this.Store);  
      ElementGroup group = new ElementGroup(element);  
  
      { // To use a shape of a default size and color, omit this block.  
        ExampleShape shape = new ExampleShape(this.Partition);  
        shape.ModelElement = element;  
        shape.AbsoluteBounds = new RectangleD(0, 0, 1.5, 1.0);  
        shape.FillColor = System.Drawing.Color.Azure;  
        group.Add(shape);  
      }  
  
      this.ElementOperations.MergeElementGroupPrototype(  
        this,  
        group.CreatePrototype(),  
        PointD.ToPointF(e.MousePosition));  
      t.Commit();  
    }  
  }  
}  
  
```  
  
 如果你提供多个形状，设置其使用的相对位置`AbsoluteBounds`。  
  
 你还可以设置颜色和其他公开的属性的连接器使用此方法。  
  
### <a name="use-transactions"></a>使用事务  
 形状、 连接器和关系图是子类型的<xref:Microsoft.VisualStudio.Modeling.ModelElement>和实时存储区中。 仅在事务内，因此必须对它们进行更改。 有关详细信息，请参阅[如何： 使用事务来更新模型](../modeling/how-to-use-transactions-to-update-the-model.md)。  
  
##  <a name="docdata"></a>文档视图和文档数据  
 ![标准关系图类型的类图](../modeling/media/dsldiagramsanddocs.png "DSLDiagramsandDocs")  
  
## <a name="store-partitions"></a>存储分区  
 加载模型后，在同一时间加载随附的关系图。 通常情况下，该模型加载到 Store.DefaultPartition，和关系图内容都加载到另一个分区。 通常情况下，每个分区的内容的加载，并保存到单独的文件中。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Modeling.ModelElement>   
 [域特定语言中的验证](../modeling/validation-in-a-domain-specific-language.md)   
 [从域特定语言生成代码](../modeling/generating-code-from-a-domain-specific-language.md)   
 [如何： 使用事务来更新模型](../modeling/how-to-use-transactions-to-update-the-model.md)   
 [通过使用 Visual Studio Modelbus 集成模型](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [响应并传播更改](../modeling/responding-to-and-propagating-changes.md)
