---
title: "How to: Add a Custom SharePoint Node to Server Explorer"
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
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
  - "SharePoint Connections [SharePoint development in Visual Studio], creating a new node type"
ms.assetid: b992a192-f926-45e6-9416-85ddfe1061d0
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# How to: Add a Custom SharePoint Node to Server Explorer
  您可以在**“服务器资源管理器”**中的**“SharePoint 连接”**节点下添加自定义节点。  当您希望显示**“服务器资源管理器”**中默认情况下未显示的其他 SharePoint 组件时，这样做很有用。  有关更多信息，请参见[Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。  
  
 若要添加自定义节点，请先创建一个定义新节点的类。  然后，创建一个用于将新节点添加为现有节点的子级的扩展。  
  
### 定义新节点  
  
1.  创建一个类库项目。  
  
2.  添加对下列程序集的引用：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
    -   System.Drawing  
  
3.  创建实现 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> 接口的类。  
  
4.  向该类添加下列特性：  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>.  此特性使 Visual Studio 能够发现和加载您的 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> 实现。  将 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> 类型传递给特性构造函数。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>.  在节点定义中，此特性指定新节点的字符串标识符。  建议您使用“*公司名称*.*节点名称*”格式以确保所有节点具有一个唯一标识符。  
  
5.  在 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> 方法的实现中，使用 *typeDefinition* 参数的成员来配置新节点的行为。  此参数是一个 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> 对象，它提供对 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> 接口中定义的事件的访问。  
  
     下面的代码示例演示如何定义新的节点。  此示例假定项目将一个名为 CustomChildNodeIcon 的图标包含为嵌入资源。  
  
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorernode.cs#6)]
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorernode.vb#6)]  
  
### 将新节点添加为现有节点的子级  
  
1.  在与节点定义相同的项目中，创建一个实现 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 接口的类。  
  
2.  给类添加 <xref:System.ComponentModel.Composition.ExportAttribute> 特性。  此特性使 Visual Studio 能够发现并加载您的 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 实现。  将 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 类型传递给特性构造函数。  
  
3.  给类添加 <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> 特性。  在节点扩展中，此特性指定要扩展的节点类型的字符串标识符。  
  
     若要指定 Visual Studio 提供的内置节点类型，请将以下枚举值之一传递给特性构造函数：  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>：使用这些值可在**“服务器资源管理器”**中指定网站连接节点（即显示网站 URL 的节点）、网站节点或所有其他父节点。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>：使用这些值可指定表示 SharePoint 网站上的单个组件的内置节点之一，如表示列表、字段或内容类型的节点。  
  
4.  在 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> 方法的实现中，处理 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> 参数的 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> 事件。  
  
5.  在 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> 事件处理程序中，将新节点添加到由事件实参参数公开的 <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> 对象的子节点集合中。  
  
     下面的代码示例演示如何在**“服务器资源管理器”**中将新节点添加为 SharePoint 网站节点的子级。  
  
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorernode.cs#7)]
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorernode.vb#7)]  
  
## 完整的示例  
 下面的代码示例提供了完整代码，用于定义一个简单节点并在**“服务器资源管理器”**中将该节点添加为 SharePoint 网站节点的子级。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorernode.cs#5)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorernode.vb#5)]  
  
## 编译代码  
 此示例假定项目将一个名为 CustomChildNodeIcon 的图标包含为嵌入资源。  此示例还需要对以下程序集的引用：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
-   System.Drawing  
  
## 部署扩展  
 若要部署**“服务器资源管理器”**扩展，请为要利用此扩展分发的程序集和任何其他文件创建 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 扩展 \(VSIX\) 包。  有关更多信息，请参见[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 请参阅  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  