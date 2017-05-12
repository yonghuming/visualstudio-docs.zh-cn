---
title: "How to: Get Data for a Built-In SharePoint Node in Server Explorer"
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
ms.assetid: 86d04e0a-c114-427e-9945-da5fa339fda4
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# How to: Get Data for a Built-In SharePoint Node in Server Explorer
  对于**“服务器资源管理器”**中的每个内置 SharePoint 节点，您可以为该节点表示的基础 SharePoint 组件获取数据。  有关更多信息，请参见[Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。  
  
## 示例  
 下面的代码示例演示如何为**“服务器资源管理器”**中列表节点表示的基础 SharePoint 列表获取数据。  默认情况下，列表节点具有**“在浏览器中查看”**上下文菜单项，您可以单击该菜单项以在 Web 浏览器中打开列表。  此示例通过添加一个可直接在 Visual Studio 中打开列表的**“View in Visual Studio”（在 Visual Studio 中查看）**上下文菜单项，从而扩展了列表节点。  代码将访问节点的列表数据来获取要在 Visual Studio 中打开的列表的 URL。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorerextensionnodeinfo.cs#10)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorerextensionnodeinfo.vb#10)]  
  
 此示例使用 SharePoint 项目服务来获取用于在 Visual Studio 中打开列表的 <xref:EnvDTE.DTE> 对象。  有关 SharePoint 项目服务的更多信息，请参见[Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)。  
  
 有关为 SharePoint 节点创建扩展的基本任务的更多信息，请参见[How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。  
  
## 编译代码  
 此示例需要对以下程序集的引用：  
  
-   EnvDTE  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
## 部署扩展  
 若要部署**“服务器资源管理器”**扩展，请为要利用此扩展分发的程序集和任何其他文件创建 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 扩展 \(VSIX\) 包。  有关更多信息，请参见[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 请参阅  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  