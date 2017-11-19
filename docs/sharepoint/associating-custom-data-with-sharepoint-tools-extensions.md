---
title: "关联自定义数据与 SharePoint 工具扩展 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], associating custom data
- project items [SharePoint development in Visual Studio], associating custom data
- SharePoint project items, associating custom data
- SharePoint projects, associating custom data
- SharePoint development in Visual Studio, extensibility features
ms.assetid: cfc87272-85a1-4c36-89e4-2662417d59ea
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3a37551f56159aaa3cda03edb6ec964a79d56da9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="associating-custom-data-with-sharepoint-tools-extensions"></a>将自定义数据与 SharePoint 工具扩展相关联
  可以将自定义数据添加到 SharePoint 工具扩展中的某些对象。 如果你想要从你的扩展中的其他代码访问更高版本的扩展的一部分中具有的数据，这非常有用。 而不是实现自定义方式存储和访问数据，可以将你的扩展中的数据关联的对象，然后以后从同一对象检索数据。  
  
 当你想要保留与 Visual Studio 中特定项相关的数据时，将自定义数据添加到对象还有有用。 只需后在 Visual Studio 中，因此你的扩展可能可以使用多个不同项时，才加载 SharePoint 工具扩展 (如项目，项目项，或**服务器资源管理器**节点) 在任何时间。 如果你有只与特定项相关的自定义数据，你可以将数据添加到表示该项的对象。  
  
 当你将自定义数据添加到在 SharePoint 工具扩展中的对象时，则不会保留数据。 对象的生存期内仅有可用的数据。 通过垃圾回收回收该对象后，数据将丢失。  
  
 在扩展的 SharePoint 项目系统中，你还可以保存仍然存在，则扩展将卸载后的字符串数据。 有关详细信息，请参阅[扩展 SharePoint 项目系统中保存数据](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。  
  
## <a name="objects-that-can-contain-custom-data"></a>可以包含自定义数据对象  
 你可以将自定义数据添加到实现 SharePoint 工具对象模型中的任何对象<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>接口。 此接口定义属性只有一个<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>，它是自定义数据对象的集合。 以下类型实现<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>  
  
## <a name="adding-and-retrieving-custom-data"></a>添加和检索自定义数据  
 若要将自定义数据添加到在 SharePoint 工具扩展中的对象，获取<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>你想要向其中添加数据，然后使用该对象的属性<xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A>方法将数据添加到对象。  
  
 若要从 SharePoint 工具扩展中的对象中检索自定义数据，请获取<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>属性对象并将其中一个的以下方法：  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>。 此方法返回**true**如果存在数据对象，或**false**如果它尚不存在。 此方法可用于检索值类型或引用类型的实例。  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>。 此方法返回的数据对象，如果退出，或**null**如果它尚不存在。 可以使用此方法仅用于检索实例的引用类型。  
  
 下面的代码示例确定某个特定数据对象是否已与项目项相关联。 如果数据对象是不与项目项关联，则该代码将添加到对象<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>项目项的属性。 若要查看此示例中的上下文中的一个更大的示例，请参阅[如何： 向自定义 SharePoint 项目项类型添加属性](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)。  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]  
  
## <a name="see-also"></a>另请参阅  
 [SharePoint 工具扩展的编程概念和功能](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [演练： 使用项模板创建的自定义操作项目项，第 1 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [演练： 扩展服务器资源管理器以显示 Web 部件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [如何： 向 SharePoint 项目中添加属性](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [如何： 将属性添加到自定义 SharePoint 项目项类型](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md   
  