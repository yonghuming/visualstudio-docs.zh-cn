---
title: "Extending the SharePoint Connections Node in Server Explorer"
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
  - "SharePoint Connections [SharePoint development in Visual Studio], extending a node"
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
  - "SharePoint Connections [SharePoint development in Visual Studio], creating a new node type"
ms.assetid: 8bfa5950-0ef4-4417-9538-cc8a5a1c35e2
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Extending the SharePoint Connections Node in Server Explorer
  通过在**服务器资源管理器** 窗口中，的 **SharePoint 连接** 节点在 Visual Studio 中，可以连接到本地 SharePoint 在开发计算机上的网站。  此节点会以分层树视图形式显示本地 SharePoint 网站的很多组件。  例如，可以查看本地网站上的列表、文档库和内容类型。有关使用**“服务器资源管理器”**连接到本地 SharePoint 网站的更多信息，请参见[使用服务器资源管理器浏览 SharePoint 连接](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)。  
  
 可以通过创建现有节点的扩展或通过创建自定义节点类型并将其添加到节点层次结构中，来扩展**“SharePoint 连接”**节点。  
  
## 用于扩展“SharePoint 连接”节点的任务  
 若要扩展现有节点，请创建实现 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 接口的 Visual Studio 扩展。  在扩展节点时，可以向节点添加功能（如您自己的快捷菜单项或自定义属性）。  有关更多信息，请参见[How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。  
  
 若要创建自定义节点类型，请创建实现 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> 接口的 Visual Studio 扩展。  如果您希望显示默认情况下在**“服务器资源管理器”**中未显示的 SharePoint 网站的组件，请创建一个自定义节点。  例如，虽然**“服务器资源管理器”**默认情况下不显示 SharePoint 网站的 Web 部件库，但您可以添加一个自定义节点用来显示该部件库。  有关更多信息，请参见[How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)和[Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。  
  
## 向节点添加自定义属性  
 在扩展节点或创建自定义节点类型时，可以向节点添加自定义属性。  选定相关节点后，所添加的自定义属性将会出现在**“属性”**窗口中。  
  
 可以向节点添加两种类型的自定义属性：  
  
-   用于显示 SharePoint 网站中的一组只读数据的属性。  此类数据描述节点表示的 SharePoint 组件。  有关演示如何执行此操作的演练，请参见[Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。  
  
-   用于显示自定义读\/写数据的属性。  有关演示如何执行此操作的代码示例，请参见[How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。  
  
## 获取内置节点的数据  
 Visual Studio 提供的所有内置节点都包含有关它们表示的 SharePoint 组件的一些数据。  例如，表示 SharePoint 网站上某个列表的节点提供了有关该列表的一些数据，如该列表的默认视图的标题和 URL。  
  
 若要访问此数据，请从表示所需节点的 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> 对象的 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 属性中检索数据对象。  该数据对象的类型取决于节点的类型。  
  
 下面的代码示例演示如何获取列表节点的数据对象。  若要在一个更大的示例上下文中查看此示例，请参见[How to: Get Data for a Built-In SharePoint Node in Server Explorer](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorerextensionnodeinfo.cs#11)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorerextensionnodeinfo.vb#11)]  
  
 下表列出每个内置节点类型的数据对象类型。  
  
|节点类型|数据对象类型|  
|----------|------------|  
|SharePoint 网站节点|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|  
|内容类型|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|  
|功能|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|  
|字段|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|  
|列表|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|  
|列表模板|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|  
|列表视图 \(Microsoft.SharePoint.SPView\)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|  
|工作流关联|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|  
|工作流模板|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|  
  
 有关使用 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 属性的更多信息，请参见[Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)。  
  
## 请参阅  
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [How to: Get Data for a Built-In SharePoint Node in Server Explorer](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [使用服务器资源管理器浏览 SharePoint 连接](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)  
  
  