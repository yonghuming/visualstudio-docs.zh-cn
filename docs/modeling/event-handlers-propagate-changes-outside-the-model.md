---
title: "事件处理程序将在模型外部更改传播 |Microsoft 文档"
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
caps.latest.revision: "18"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 29c8594b80c55eb000d70f05d35bbf28becb6e26
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>事件处理程序在模型外部传播更改
在可视化和建模 SDK，你可以定义存储事件处理程序以将更改传播到应用商店中，如非应用商店变量、 文件、 模型中其他存储或其他外部资源[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]扩展。 存储事件处理程序将在其中触发的事件发生在事务结束后执行。 它们还将撤消或重做操作进行执行。 因此，与应用商店规则不同存储事件是最适用于更新存储之外的值。 与.NET 事件不同存储事件处理程序注册来侦听类： 无需注册每个实例的单独处理。 有关如何选择不同的方式来处理更改之间的详细信息，请参阅[响应和传播更改](../modeling/responding-to-and-propagating-changes.md)。  
  
 图形面和其他用户界面控件是可以由存储事件的外部资源的示例。  
  
### <a name="to-define-a-store-event"></a>若要定义一个存储事件  
  
1.  选择你想要监视的事件的类型。 有关完整列表，请查看的属性<xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>。 每个属性对应于事件的类型。 最常用的类型的事件：  
  
    -   `ElementAdded`-当模型元素时触发，关系链接、 形状或连接器创建。  
  
    -   ElementPropertyChanged-触发时的值`Normal`更改域属性。 仅当新和旧值不相等，则触发事件。 事件不能应用于计算和自定义存储属性。  
  
         它不能应用于关系链接到相对应的角色属性。 请改用`ElementAdded`要监视的域关系。  
  
    -   `ElementDeleted`-在将模型元素后触发，关系、 形状或连接器已被删除。 你仍可访问属性值的元素，但它将具有的其他元素之间没有关系。  
  
2.  添加的分部类定义*YourDsl***DocData**单独的代码文件中**DslPackage**项目。  
  
3.  将事件的代码编写为方法，如以下示例所示。 它可以是`static`，除非你想要访问`DocData`。  
  
4.  重写`OnDocumentLoaded()`注册处理程序。 如果你有多个处理程序，你可以在同一位置的所有注册它们。  
  
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
      base.OnDocumentLoaded(); // Don't forget this.  
  
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
  
## <a name="using-events-to-make-undoable-adjustments-in-the-store"></a>使用事件进行存储区中的可撤消调整  
 存储事件不通常会使用传播更改在存储，因为事件处理程序执行提交事务后。 相反，你将使用的存储规则。 有关详细信息，请参阅[规则传播更改内模型](../modeling/rules-propagate-changes-within-the-model.md)。  
  
 但是，你可以使用事件处理程序以其他更新为存储后，如果你希望用户能够撤消独立于原始事件的其他更新。 例如，假设小写字符都是唱片集标题的常用约定。 你可以编写的应用商店事件处理程序后用户已键入它以大写形式更正为小写的标题。 但是，用户可以使用撤消命令来取消你更正还原大写字符。 第二个撤消将删除用户的更改。  
  
 与此相反，如果你编写的应用商店规则来执行相同操作，用户的更改和你更正应在同一事务中，以便用户无法撤消此调整而不会失去原始的更改。  
  
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
  
 如果你编写更新存储区的事件：  
  
-   使用`store.InUndoRedoOrRollback`若要避免更改中撤消的模型元素。 事务管理器将设置所有内容恢复到其原始状态存储中。  
  
-   使用`store.InSerializationTransaction`若要避免从文件加载模型时更改。  
  
-   所做的更改将导致进一步的事件触发。 请确保你避免无限循环。  
  
## <a name="store-event-types"></a>存储事件类型  
 每个事件类型对应于 Store.EventManagerDirectory 中的集合。 你可以添加或移除事件处理程序在任意时间，但通常将文档加载时添加它们。  
  
|`EventManagerDirectory`属性名称|时执行|  
|-------------------------------------------|-------------------|  
|ElementAdded|创建域类、 域关系、 形状、 连接器或关系图的实例。|  
|ElementDeleted|将模型元素已从存储区的元素目录中删除并且不再的源或目标的任何关系。 元素不实际从内存中删除，但会保留发生将来撤消。|  
|ElementEventsBegun|调用外部事务的末尾。|  
|ElementEventsEnded|尚未处理所有其他事件时调用。|  
|ElementMoved|将模型元素已从一个存储区分区移动到另一个。<br /><br /> 这不被与关系图上形状的位置。|  
|ElementPropertyChanged|域属性的值已更改。 仅当旧和新值不相等时执行此操作。|  
|RolePlayerChanged|关系的两个角色 （结束） 之一引用了新元素。|  
|RolePlayerOrderChanged|具有多重性大于 1 的角色，在已更改的链接的序列。|  
|TransactionBeginning||  
|TransactionCommitted||  
|TransactionRolledBack||  
  
## <a name="see-also"></a>另请参阅  
 [响应并且将更改传播](../modeling/responding-to-and-propagating-changes.md)   
 [示例代码： 线路关系图](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
 
