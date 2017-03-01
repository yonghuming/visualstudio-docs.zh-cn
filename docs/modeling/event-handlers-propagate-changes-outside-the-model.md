---
title: "事件处理程序将在模型外部的更改传播 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
ms.assetid: 0ac8d1e4-239f-4370-ba1d-3769bb38b8a5
caps.latest.revision: 18
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: af5fbd8973082e92f9609e335314a30eb22595fa
ms.lasthandoff: 02/22/2017

---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>事件处理程序在模型外部传播更改
在可视化和建模 SDK，您可以定义存储事件处理程序以将更改传播到存储区，如非存储变量、 文件、 模型中其他商店，或其他外部资源[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]扩展。 存储事件处理程序触发的事件发生在事务结束之后执行。 它们也是在撤消或重做操作中执行的。 因此，存储区与规则不同，存储事件是最适用于更新商店外的值。 与.NET 事件不同存储事件处理程序被注册来侦听到的类︰ 无需注册每个实例的单独处理。 有关如何选择不同的方式来处理更改之间的详细信息，请参阅[响应并传播更改](../modeling/responding-to-and-propagating-changes.md)。  
  
 图形的外围应用和其他用户界面控件是可由存储事件的外部资源的示例。  
  
### <a name="to-define-a-store-event"></a>若要定义存储事件  
  
1.  选择您想要监视的事件的类型。 有关完整列表，查看<xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>。</xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>属性 每个属性对应于事件的类型。 最常用的事件类型包括︰  
  
    -   `ElementAdded`– 当模型元素时，触发，关系链接、 形状或连接线创建。  
  
    -   ElementPropertyChanged – 触发时的值`Normal`更改域属性。 仅当新、 旧值不相等，则触发事件。 该事件不能应用于计算和自定义存储属性。  
  
         它不能应用于对应于关系链接的角色属性。 请改用`ElementAdded`来监视域之间的关系。  
  
    -   `ElementDeleted`– 触发后的模型元素、 关系、 形状或连接线已被删除。 您仍可以访问该元素的属性值，但它将没有任何关系的其他元素。  
  
2.  添加的分部类定义*YourDsl***DocData**单独的代码文件中**DslPackage**项目。  
  
3.  作为方法，如以下示例所示编写的事件的代码。 它可以是`static`，除非您想要访问`DocData`。  
  
4.  重写`OnDocumentLoaded()`注册处理程序。 如果您有多个处理程序，可以在同一个位置进行注册。  
  
 注册代码的位置并不重要。 `DocView.LoadView()`是另一个位置。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Microsoft.VisualStudio.Modeling;  
  
namespace Company.MusicLib  
{  
  partial class MusicLibDocData  
  {  
    // Register store events here or in DocView.LoadView().  
    protected override void OnDocumentLoaded()  
    {  
      base.OnDocumentLoaded(); // Don’t forget this.  
  
      #region Store event handler registration.       
      Store store = this.Store;  
      EventManagerDirectory emd = store.EventManagerDirectory;  
      DomainRelationshipInfo linkInfo = store.DomainDataDirectory  
          .FindDomainRelationship(typeof(ArtistAppearsInAlbum));  
      emd.ElementAdded.Add(linkInfo,   
          new EventHandler<ElementAddedEventArgs>(AddLink));  
      emd.ElementDeleted.Add(linkInfo,   
          new EventHandler<ElementDeletedEventArgs>(RemoveLink));  
  
      #endregion Store event handlers.  
    }  
  
    private void AddLink(object sender, ElementAddedEventArgs e)  
    {  
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;  
      if (link != null)   
            ExternalDatabase.Add(link.Artist.Name, link.Album.Title);  
    }  
    private void RemoveLink(object sender, ElementDeletedEventArgs e)  
    {  
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;  
      if (link != null)   
            ExternalDatabase.Delete(link.Artist.Name, link.Album.Title);  
    }  
  }  
  
}  
  
```  
  
## <a name="using-events-to-make-undoable-adjustments-in-the-store"></a>使用事件来调整可撤消在存储区  
 存储事件不通常用于传播更改，在存储，因为该事件处理程序的执行速度提交事务后。 相反，将使用的存储规则。 有关详细信息，请参阅[规则传播的更改中的模式](../modeling/rules-propagate-changes-within-the-model.md)。  
  
 但是，您可以使用事件处理程序来做其他更新，到存储区中，如果您希望用户能够撤消独立于原始事件的其他更新。 例如，假设小写字符唱片集标题的常规惯例。 您可以编写的存储事件处理程序后用户已以大写形式键入其更正为小写的标题。 但用户可以使用撤消命令以取消您更正还原大写字符。 第二个撤消会删除用户的更改。  
  
 与此相反，如果您编写了一个存储区规则，以执行相同的操作，用户的更改和您更正应该在同一事务中，以便用户无法撤消调整而不会丢失原始的更改。  
  
```  
  
partial class MusicLibDocView  
{  
    // Register store events here or in DocData.OnDocumentLoaded().  
    protected override void LoadView()  
    {  
      /* Register store event handler for Album Title property. */  
      // Get reflection data for property:  
      DomainPropertyInfo propertyInfo =   
        this.DocData.Store.DomainDataDirectory  
        .FindDomainProperty(Album.TitleDomainPropertyId);  
      // Add to property handler list:  
      this.DocData.Store.EventManagerDirectory  
        .ElementPropertyChanged.Add(propertyInfo,  
        new EventHandler<ElementPropertyChangedEventArgs>  
             (AlbumTitleAdjuster));  
  
      /*  
      // Alternatively, you can set one handler for   
      // all properties of a class.  
      // Your handler has to determine which property changed.  
      DomainClassInfo classInfo = this.Store.DomainDataDirectory  
           .FindDomainClass(typeof(Album));  
      this.Store.EventManagerDirectory  
          .ElementPropertyChanged.Add(classInfo,  
        new EventHandler<ElementPropertyChangedEventArgs>  
             (AlbumTitleAdjuster));  
       */  
      return base.LoadView();  
    }  
  
// Undoable adjustment after a property is changed.   
// Method can be static since no local access.  
private static void AlbumTitleAdjuster(object sender,  
         ElementPropertyChangedEventArgs e)  
{  
  Album album = e.ModelElement as Album;  
  Store store = album.Store;  
  
  // We mustn't update the store in an Undo:  
  if (store.InUndoRedoOrRollback   
      || store.InSerializationTransaction)  
      return;  
  
  if (e.DomainProperty.Id == Album.TitleDomainPropertyId)  
  {  
    string newValue = (string)e.NewValue;  
    string lowerCase = newValue.ToLowerInvariant();  
    if (!newValue.Equals(lowerCase))  
    {  
      using (Transaction t = store.TransactionManager  
            .BeginTransaction("adjust album title"))  
      {  
        album.Title = lowerCase;  
        t.Commit();  
      } // Beware! This could trigger the event again.  
    }  
  }  
  // else other properties of this class.  
}  
  
```  
  
 如果您编写一个事件，更新存储区︰  
  
-   使用`store.InUndoRedoOrRollback`以避免对中撤消的模型元素进行更改。 事务管理器将所有内容设置回其原始状态存储区中。  
  
-   使用`store.InSerializationTransaction`以避免在从文件加载模型时进行更改。  
  
-   所做的更改将导致更多的事件触发。 请确保避免出现无限循环。  
  
## <a name="store-event-types"></a>存储事件类型  
 每个事件类型对应于在 Store.EventManagerDirectory 的集合。 您可以添加或移除事件处理程序在任何时候，但通常将文档加载时添加它们。  
  
|`EventManagerDirectory`属性名称|时执行|  
|-------------------------------------------|-------------------|  
|ElementAdded|创建域类、 域之间的关系、 形状、 连接符或关系图的实例。|  
|ElementDeleted|模型元素已从存储的元素目录中删除，并且不再的源或目标的任何关系。 该元素不会从内存中，实际删除，但会保留将来撤消发生。|  
|ElementEventsBegun|调用外部事务的末尾。|  
|ElementEventsEnded|所有其他事件已得到处理时调用。|  
|ElementMoved|模型元素已从一个存储分区移动到另一个。<br /><br /> 这没有与关系图上形状的位置。|  
|ElementPropertyChanged|域属性的值已更改。 这被执行仅当旧的和新值不相等。|  
|RolePlayerChanged|一种关系的两个角色 （结尾） 之一引用了一个新的元素。|  
|RolePlayerOrderChanged|具有重数大于 1 的角色，在已更改的链接的序列。|  
|TransactionBeginning||  
|TransactionCommitted||  
|TransactionRolledBack||  
  
## <a name="see-also"></a>另请参阅  
 [响应并传播更改](../modeling/responding-to-and-propagating-changes.md)   
 [示例代码︰ 电路图](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
 

