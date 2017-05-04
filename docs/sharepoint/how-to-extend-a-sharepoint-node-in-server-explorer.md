---
title: "How to: Extend a SharePoint Node in Server Explorer | Microsoft Docs"
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
ms.assetid: 5e443950-12e6-40d1-864b-c384b6be4ce4
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# How to: Extend a SharePoint Node in Server Explorer
  您可以在**“服务器资源管理器”**中的**“SharePoint 连接”**节点下扩展节点。  这对于需要向现有节点中添加新的子节点、快捷菜单项或属性的情况非常有用。  有关更多信息，请参见[Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。  
  
### 扩展服务器资源管理器中的 SharePoint 节点  
  
1.  创建一个类库项目。  
  
2.  添加对下列程序集的引用：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
3.  创建一个实现 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 接口的类。  
  
4.  给类添加 <xref:System.ComponentModel.Composition.ExportAttribute> 特性。  此特性使 Visual Studio 能够发现并加载您的 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 实现。  将 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 类型传递给特性构造函数。  
  
5.  给类添加 <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> 特性。  此特性指定要扩展的节点类型的字符串标识符。  
  
     若要指定 Visual Studio 提供的内置节点类型，请将以下枚举值之一传递给特性构造函数：  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>：使用这些值可在**“服务器资源管理器”**中指定网站连接节点（即显示网站 URL 的节点）、网站节点或所有其他父节点。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>：使用这些值可指定表示 SharePoint 网站上的单个组件的内置节点之一，如表示列表、字段或内容类型的节点。  
  
6.  在 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> 方法的实现中，使用 *nodeType* 参数的成员以将功能添加到节点中。  此参数是一个 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> 对象，它提供对 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> 接口中定义的事件的访问。  例如，您可以处理以下事件：  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>：处理此事件可将新的子节点添加到节点中。  有关更多信息，请参见[How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>：处理此事件可将自定义快捷菜单项添加到节点中。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>：处理此事件可将自定义属性添加到节点中。  选定相关节点后，所添加的自定义属性将会出现在**“属性”**窗口中。  
  
## 示例  
 下面的代码示例演示如何创建两种不同类型的节点扩展：  
  
-   将上下文菜单项添加到 SharePoint 网站节点的扩展。  当单击菜单项时，它显示所单击节点的名称。  
  
-   将名为**“ContosoExampleProperty”**的自定义属性添加到表示名为**“Body”**的字段的每个节点的扩展。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorerextension.cs#9)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorerextension.vb#9)]  
  
 此扩展会将可编辑的字符串属性添加到节点中。  还可以创建用于显示 SharePoint 服务器的只读数据的自定义属性。  有关演示如何执行此操作的示例，请参见[Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。  
  
## 编译代码  
 此示例需要对以下程序集的引用：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
-   System.Windows.Forms  
  
## 部署扩展  
 若要部署**“服务器资源管理器”**扩展，请为要利用此扩展分发的程序集和任何其他文件创建 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 扩展 \(VSIX\) 包。  有关更多信息，请参见[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 请参阅  
 [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  