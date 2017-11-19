---
title: "如何： 扩展服务器资源管理器中的 SharePoint 节点 |Microsoft 文档"
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
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
ms.assetid: 5e443950-12e6-40d1-864b-c384b6be4ce4
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 98dd11e74053bde9ad1ec2e23f4f663dfa7d1e1d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>如何：扩展服务器资源管理器中的 SharePoint 节点
  你可以扩展下的子节点**SharePoint 连接**中的节点**服务器资源管理器**。 当你想要将新的子节点、 快捷方式菜单项或属性添加到现有节点时，这非常有用。 有关详细信息，请参阅[扩展服务器资源管理器中的 SharePoint 连接节点](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。  
  
### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>若要扩展服务器资源管理器中的 SharePoint 节点  
  
1.  创建类库项目。  
  
2.  添加对下列程序集的引用：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
3.  创建实现 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 接口的类。  
  
4.  添加<xref:System.ComponentModel.Composition.ExportAttribute>到类属性。 此属性使 Visual Studio 发现和加载你<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>实现。 传递<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>给特性构造函数的类型。  
  
5.  添加<xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>到类属性。 此属性指定你想要扩展的节点的类型的字符串标识符。  
  
     若要指定由 Visual Studio 提供的内置节点类型，请将下面的枚举值之一传递给特性构造函数：  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>： 使用这些值来指定站点连接节点 （节点显示站点 Url），站点中的所有其他父节点或节点，**服务器资源管理器**。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>： 使用这些值可指定其中一个内置节点表示 SharePoint 站点，如表示列表、 字段或内容类型的节点上的单个组件。  
  
6.  实现中<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A>方法，使用成员*nodeType*参数将功能添加到节点。 此参数是<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>提供对中定义的事件的访问的对象<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents>接口。 例如，你可以处理以下事件：  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>： 处理此事件以将新的子节点添加到节点。 有关详细信息，请参阅[如何： 向服务器资源管理器中添加自定义 SharePoint 节点](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>： 处理此事件以将自定义的快捷菜单项添加到节点。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>： 处理此事件以将自定义属性添加到节点。 属性将显示在**属性**窗口时选择的节点。  
  
## <a name="example"></a>示例  
 下面的代码示例演示如何创建两个不同类型的节点扩展：  
  
-   将一个上下文菜单项添加到 SharePoint 站点节点扩展。 单击菜单项时，它将显示被单击的节点的名称。  
  
-   将添加名为的自定义属性扩展**ContosoExampleProperty**表示名为的字段的每个节点到**正文**。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs#9)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb#9)]  
  
 此扩展添加到节点的可编辑的字符串属性。 你还可以创建显示 SharePoint server 的只读数据的自定义属性。 有关演示如何执行此操作的示例，请参阅[演练： 扩展服务器资源管理器显示 Web 部件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要引用以下程序集：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
-   System.Windows.Forms  
  
## <a name="deploying-the-extension"></a>部署扩展  
 若要部署**服务器资源管理器**扩展，创建[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]扩展 (VSIX) 包的程序集和你想要随此扩展分发的任何其他文件。 有关详细信息，请参阅[部署 Visual Studio 中的 SharePoint 工具扩展](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 向服务器资源管理器中添加自定义 SharePoint 节点](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [扩展服务器资源管理器中的 SharePoint 连接节点](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [演练： 扩展服务器资源管理器以显示 Web 部件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [将自定义数据与 SharePoint 工具扩展相关联](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  