---
title: "自定义删除行为 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.dsldesigner.deletebehavior
helpviewer_keywords: Domain-Specific Language, deletion
ms.assetid: c6bf088d-52c6-4817-af45-ddae745bb5a9
caps.latest.revision: "23"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 159d6a7b3a381eeb5d6f92154e657de67c567a38
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="customizing-deletion-behavior"></a>自定义删除行为
删除一个元素通常会导致同时删除相关的元素。 将删除连接到该元素的所有关系以及任何子元素。 此行为名为*删除传播*。 可以自定义删除传播，例如安排删除其他相关元素。 通过编写程序代码，可以根据模型的状态删除传播。 还可能发生其他更改以响应删除。  
  
 本主题包括以下部分：  
  
-   [默认删除行为](#default)  
  
-   [设置角色的传播删除选项](#property)  
  
-   [重写删除闭包](#closure)-使用此方法删除可能导致删除的相邻元素。  
  
-   [使用 OnDeleting 和 OnDeleted](#ondeleting) -使用这些方法响应其中可能包括其他操作，例如更新内部或外部存储的值。  
  
-   [删除规则](#rules)-使用规则传播在存储区，其中一项更改可能会导致其他任何类型的更新。  
  
-   [删除事件](#rules)-使用存储事件传播 store 外的例如对其他更新[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]文档。  
  
-   [取消合并](#unmerge)-取消合并操作用于撤消附加到其父级的子元素的合并操作。  
  
##  <a name="default"></a>默认删除行为  
 默认情况下，以下规则控制删除传播：  
  
-   如果删除某个元素，也将删除所有嵌入元素。 嵌入元素是作为嵌入关系的目标的元素，而此元素是嵌入关系的源。 例如，如果没有从嵌入关系**唱片集**到**首歌曲**，然后当删除特定唱片集时，也将删除所有歌曲。  
  
     相反，删除 Song 并不会删除 Album。  
  
-   默认情况下，删除不会沿着引用关系传播。 如果不存在引用关系**ArtistPlaysOnAlbum**从**唱片集**到**艺术家**、 删除唱片集不会删除任何相关的艺术家和删除艺术家不删除任何唱片集。  
  
     但是，删除将沿着一些内置关系传播。 例如，当删除模型元素时，还将删除它在关系图上的形状。 元素和形状通过 `PresentationViewsSubject` 引用关系相关联。  
  
-   不管是在源角色上还是在目标角色上，都将删除连接到该元素的每个关系。 对方角色的元素的角色属性不再包含删除的元素。  
  
##  <a name="property"></a>设置角色的传播删除选项  
 可以使删除沿着引用关系传播，或从嵌入子级传播到其父级。  
  
#### <a name="to-set-delete-propagation"></a>设置删除传播  
  
1.  DSL 定义关系图中，在选择*角色*到你想要删除的传播。 该角色由域关系框的左侧或右侧的线表示。  
  
     例如，如果想要指定在删除 Album 时，也将删除相关的 Artist，则选择已连接到域类 Artist 的角色。  
  
2.  在属性窗口中，设置**传播删除**属性。  
  
3.  按 F5 并验证：  
  
    -   当删除此关系的实例时，也将删除选定角色的元素。  
  
    -   当删除对方角色的元素时，将删除此关系的实例，也将删除此角色的相关元素。  
  
 你还可以看到**传播删除**选项**DSL 详细信息**窗口。 选择域类，然后在 DSL 详细信息窗口中，打开**删除行为**页上通过单击按钮在窗口的一侧。 **传播**选项显示为每个关系的相反的角色。 **删除样式**列指示是否**传播**选项为默认设置，但它不具有任何单独的效果。  
  
## <a name="delete-propagation-by-using-program-code"></a>通过使用程序代码删除传播  
 DSL 定义文件中的选项仅允许你选择是否将删除传播到邻近内容。 若要实现删除传播的更复杂方案，你可以编写程序代码。  
  
> [!NOTE]
>  若要将程序代码添加到你的 DSL 定义，创建另一个代码文件中的**Dsl**项目，然后编写分部定义来加强生成的代码文件夹中的类。 有关详细信息，请参阅[编写代码，以自域特定语言](../modeling/writing-code-to-customise-a-domain-specific-language.md)。  
  
##  <a name="closure"></a>定义一个删除闭包  
 删除操作使用类*YourModel***DeleteClosure**来确定要删除给定的初始选择哪些元素。 它将重复调用 `ShouldVisitRelationship()` 和 `ShouldVisitRolePlayer()`，从而遍历这些关系图。 可以重写这些方法。 ShouldVisitRolePlayer 提供的链接的元素和位于该链接的角色之一的标识。 它应返回以下值之一：  
  
-   **VisitorFilterResult.Yes**-应当删除元素并查看器应继续尝试元素的其他链接。  
  
-   **VisitorFilterResult.DoNotCare** -除非另一个查询答复其应被删除，不应删除元素。  
  
-   **VisitorFilterResult.Never** -元素一定不会被删除，即使另一个查询接听**是**，查看器也不应尝试和元素的其他链接。  
  
```  
// When a musician is deleted, delete their albums with a low rating.  
// Override methods in <YourDsl>DeleteClosure in DomainModel.cs  
partial class MusicLibDeleteClosure  
{  
  public override VisitorFilterResult ShouldVisitRolePlayer  
    (ElementWalker walker, ModelElement sourceElement, ElementLink elementLink,   
    DomainRoleInfo targetDomainRole, ModelElement targetRolePlayer)  
  {  
    ArtistAppearsInAlbum link = elementLink as ArtistAppearsInAlbum;  
    if (link != null   
       && targetDomainRole.RolePlayer.Id == Album.DomainClassId)  
    {  
      // Count other unvisited links to the Album of this link.  
      if (ArtistAppearsInAlbum.GetLinksToArtists(link.Album)  
              .Where(linkAlbumArtist =>   
                     linkAlbumArtist != link &&  
                     !walker.Visited(linkAlbumArtist))  
              .Count() == 0)  
      {  
        // Should delete this role player:  
        return VisitorFilterResult.Yes;   
      }  
      else  
        // Don't delete unless another relationship deletes it:  
        return VisitorFilterResult.DoNotCare;   
    }  
    else   
    {  
      // Test for and respond to other relationships and roles here.  
  
      // Not the relationship or role we're interested in.  
      return base.ShouldVisitRolePlayer(walker, sourceElement,   
             elementLink, targetDomainRole, targetRolePlayer);  
    }  
  }  
}  
  
```  
  
 闭包技术可确保在开始删除之前确定要删除的元素和链接集。 查看器还将闭包的结果和来自模型其他部分的结果组合在一起。  
  
 但是，该技术假设删除在关系图中仅影响其邻近内容：无法使用此方法删除模型的另一部分中的元素。 如果想要添加元素或进行其他更改以响应删除，则不能使用此技术。  
  
##  <a name="ondeleting"></a>使用 OnDeleting 和 OnDeleted  
 可以在域类或域关系中重写 `OnDeleting()` 或 `OnDeleted()`。  
  
1.  在将要删除元素时，但在该元素的关系已断开连接前，调用 <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleting%2A>。 该元素仍可在其他元素中来回导航，并且仍位于 `store.ElementDirectory` 中。  
  
     如果同时删除多个元素，则在执行删除操作前为所有元素调用 OnDeleting。  
  
     `IsDeleting` 为 true。  
  
2.  已删除该元素后，调用 <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleted%2A>。 它将保留在 CLR 堆中，以便在需要时可执行“撤消”，但它已与其他元素取消链接并已从 `store.ElementDirectory` 中删除。 对于关系，角色仍然引用旧角色扮演者。`IsDeleted` 也是如此。  
  
3.  当用户在创建元素后调用“撤消”时，以及在“重做”中重复以前的删除时，将调用 OnDeleting 和 OnDeleted。 使用 `this.Store.InUndoRedoOrRollback` 来避免在这些情况下更新存储元素。 有关详细信息，请参阅[如何： 使用事务来更新模型](../modeling/how-to-use-transactions-to-update-the-model.md)。  
  
 例如，以下代码将在删除 Album 的最后一个子级 Song 时删除该 Album：  
  
```  
  
// Delete the parent Album when the last Song is deleted.  
// Override methods in the embedding relationship between Album and Song:  
partial class AlbumHasSongs  
{  
  protected override void OnDeleted()  
  {  
    base.OnDeleted();  
    // Don't perform in-store actions in undo:  
    if (this.Store.InUndoRedoOrRollback) return;  
    // Relationship source and target still work:  
    // Don't bother if source is already on its way out:  
    if (!this.Album.IsDeleting && !this.Album.IsDeleted)  
    {  
      if (this.Album.Songs.Count == 0)  
      {   
        this.Album.Delete();  
} } } }  
  
```  
  
 从关系的删除触发通常比从角色元素触发更有用，因为这将同时在删除元素和删除关系本身时起作用。 但是，对于引用关系，你可能想要在删除相关元素时而不是在删除关系本身时传播删除。 此示例将在删除 Album 的最后一个参与的 Artist 时删除该 Album，但它不会在删除关系时响应：  
  
```  
using System.Linq; ...  
// Assumes a many-many reference relationship   
// between Artist and Album.    
partial class Artist  
{  
  protected override void OnDeleting()  
  {  
    base.OnDeleting();  
    if (this.Store.InUndoRedoOrRollback) return;  
    List<Album> toDelete = new List<Album>();  
    foreach (Album album in this.Albums)  
    {  
      if (album.Artists.Where(artist => !artist.IsDeleting)  
                        .Count() == 0)  
      {  
        toDelete.Add(album);  
      }  
    }  
    foreach (Album album in toDelete)  
    {  
      album.Delete();  
} } }  
  
```  
  
 当在元素上执行 <xref:Microsoft.VisualStudio.Modeling.ModelElement.Delete%2A> 时，将调用 OnDeleting 和 OnDeleted。 这些方法将始终执行以内联方式-即，立即之前和之后实际删除。 如果代码将删除两个或多个元素，则将在所有元素上按顺序交替调用 OnDeleting 和 OnDeleted。  
  
##  <a name="rules"></a>删除规则和事件  
 作为 OnDelete 处理程序的替代方法，你可以定义删除规则和删除事件。  
  
1.  **删除**和**删除**仅在一个事务，并且不在撤消或重做操作触发的规则。 可以设置它们以进行排队，从而在执行删除的事务末尾执行它们。 Deleting 规则始终在队列中的任何 Deleted 规则之前执行。  
  
     使用规则来传播仅影响存储中的元素的更改，包括关系、关系图元素及其属性。 通常，Deleting 规则用于传播删除，而 Delete 规则用于创建替换元素和关系。  
  
     有关详细信息，请参阅[规则传播更改内模型](../modeling/rules-propagate-changes-within-the-model.md)。  
  
2.  **删除**存储事件的事务，末尾调用和撤消或重做后调用。 因此，它可以用于将删除传播到存储外的对象，例如文件、数据库项或 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的其他对象。  
  
     有关详细信息，请参阅[事件处理程序传播更改外部模型](../modeling/event-handlers-propagate-changes-outside-the-model.md)。  
  
    > [!WARNING]
    >  已删除某个元素后，可以访问其域属性值，但无法导航关系链接。 但是，如果在关系上设置了 Deleted 事件，则还可以访问作为其角色扮演者的两个元素。 因此，如果你想要响应与模型元素的删除操作，但想要访问链接到的元素，则可设置而不是模型元素的域类关系上删除事件。  
  
### <a name="example-deletion-rules"></a>示例 Deletion 规则  
  
```  
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]  
internal class AlbumDeletingRule : DeletingRule  
{  
  public override void ElementDeleting(ElementDeletingEventArgs e)  
  {  
    base.ElementDeleting(e);  
    // ...perform tasks to propagate imminent deletion  
  }  
}  
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]  
internal class AlbumDeletedRule : DeleteRule  
{  
  public override void ElementDeleted(ElementDeletedEventArgs e)  
  {  
    base.ElementDeleted(e);  
    // ...perform tasks such as creating new elements  
  }  
}  
  
// The rule must be registered:  
public partial class MusicLibDomainModel  
{  
  protected override Type[] GetCustomDomainModelTypes()  
  {  
    List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
    types.Add(typeof(AlbumDeletingRule));  
    types.Add(typeof(AlbumDeletedRule));  
    // If you add more rules, list them here.   
    return types.ToArray();  
  }  
}  
  
```  
  
### <a name="example-deleted-event"></a>示例 Deleted 事件  
  
```  
partial class NestedShapesSampleDocData  
{  
  protected override void OnDocumentLoaded(EventArgs e)  
  {  
    base.OnDocumentLoaded(e);  
    DomainRelationshipInfo commentRelationship =   
          this.Store.DomainDataDirectory  
          .FindDomainRelationship(typeof(CommentsReferenceComponents));  
  
    this.Store.EventManagerDirectory.ElementDeleted.Add(commentRelationship,  
      new EventHandler<ElementDeletedEventArgs>(CommentLinkDeleted));  
  }  
  
  private void CommentLinkDeleted (object sender, ElementDeletedEventArgs e)  
  {  
    CommentsReferenceComponents link = e.ModelElement as CommentsReferenceComponents;  
    Comment comment = link.Comment;  
    Component component = link.Subject;  
    if (comment.IsDeleted)  
    {  
      // The link was deleted because the comment was deleted.  
      System.Windows.Forms.MessageBox.Show("Removed comment on " + component.Name);  
    }  
    else  
    {  
      // It was just the link that was deleted - the comment itself remains.  
      System.Windows.Forms.MessageBox.Show("Removed comment link to "   
           + component.Name);  
    }  
  }  
}  
  
```  
  
##  <a name="unmerge"></a>取消合并  
 将子元素附加到其父级的操作称为*合并*。 当从工具箱创建新元素或元素组时、从模型的另一个部分进行移动时，或从剪贴板进行复制时，将会发生此情况。 除了在父级和其新子级之间创建嵌入关系，合并操作还可以设置其他关系、创建辅助元素以及设置元素中的属性值。 合并操作封装在元素合并指令 (EMD) 中。  
  
 EMD 也会封装补充*取消合并*或`MergeDisconnect`操作。 如果你具有已通过使用合并构造的元素的群集，则建议使用关联的取消合并将元素从该群集中移除（如果想要使剩余元素保留在一致的状态下）。 通常，取消合并操作将使用前面部分中所述的技术。  
  
 有关详细信息，请参阅[移动数据和自定义元素创建](../modeling/customizing-element-creation-and-movement.md)。  
  
## <a name="see-also"></a>另请参阅  
 [自定义复制行为](../modeling/customizing-copy-behavior.md)   
 [自定义元素创建和移动](../modeling/customizing-element-creation-and-movement.md)   
 [编写代码以自定义域特定语言](../modeling/writing-code-to-customise-a-domain-specific-language.md)