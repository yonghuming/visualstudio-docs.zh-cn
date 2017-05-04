---
title: "Associating Custom Data with SharePoint Tools Extensions | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "projects [SharePoint development in Visual Studio], associating custom data"
  - "project items [SharePoint development in Visual Studio], associating custom data"
  - "SharePoint project items, associating custom data"
  - "SharePoint projects, associating custom data"
  - "SharePoint development in Visual Studio, extensibility features"
ms.assetid: cfc87272-85a1-4c36-89e4-2662417d59ea
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Associating Custom Data with SharePoint Tools Extensions
  可以向 SharePoint 工具扩展中的某些对象添加自定义数据。  如果您的数据位于扩展的一部分中，而稍后您想从扩展中的其他代码访问该数据，则建立关联对于这种情况非常有用。  您可以将数据与扩展中的某个对象相关联，然后从相同的对象检索数据，而不是实现一种用于存储和访问数据的自定义方式。  
  
 向对象中添加自定义数据对于您希望保留与 Visual Studio 中特定项相关的数据这种情况也非常有用。  由于 SharePoint 工具扩展在 Visual Studio 中只加载一次，因此您的扩展随时可能会用于多个不同的项（如项目、项目项或 **Server Explorer** 节点）。  如果您的自定义数据只与特定项相关，则可以将该数据添加到表示该项的对象中。  
  
 在向 SharePoint 工具扩展中的对象添加自定义数据时，该数据不会保留。  该数据仅在该对象的生存期内可用。  在垃圾回收功能将该对象回收之后，数据将丢失。  
  
 在 SharePoint 项目系统的扩展中，还可以保存在卸载扩展后继续存在的字符串数据。  有关更多信息，请参见[Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。  
  
## 可包含自定义数据的对象  
 可以将自定义数据添加到 SharePoint 工具对象模型中实现 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> 接口的任何对象。  此接口只定义一个属性（即 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>），该属性是自定义数据对象的集合。  以下类型实现 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>：  
  
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
  
## 添加和检索自定义数据  
 若要将自定义数据添加到 SharePoint 工具扩展中的某个对象，请获取要将数据添加到的对象的 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 属性，然后使用 <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> 方法将数据添加到该对象中。  
  
 若要从 SharePoint 工具扩展中的某个对象检索自定义数据，请获取该对象的 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 属性，然后使用下列方法之一：  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>.  如果该数据对象存在，则此方法返回 **true**；如果该数据对象不存在，则返回 **false**。  可以使用此方法检索值类型或引用类型的实例。  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>.  如果该数据对象存在，则此方法返回该数据对象；如果该数据对象不存在，则返回 **null**。  可以使用此方法仅检索引用类型的实例。  
  
 下面的代码示例确定某个特定数据对象是否已与一个项目项相关联。  如果该数据对象尚未与该项目项相关联，则代码会将该对象添加到该项目项的 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 属性中。  若要在一个更大的示例上下文中查看此示例，请参见[How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypeproperty.cs#13)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypeproperty.vb#13)]  
  
## 请参阅  
 [Programming Concepts and Features for SharePoint Tools Extensions](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)  
  
  