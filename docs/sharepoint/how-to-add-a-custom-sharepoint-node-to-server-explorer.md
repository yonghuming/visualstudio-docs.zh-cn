---
title: "如何： 将自定义 SharePoint 节点添加到服务器资源管理器 |Microsoft 文档"
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
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
ms.assetid: b992a192-f926-45e6-9416-85ddfe1061d0
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7aa3ccbeaae231b0abf4885c592addc586ccfb28
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>如何：向服务器资源管理器添加自定义 SharePoint 节点
  你可以自定义下添加节点**SharePoint 连接**中的节点**服务器资源管理器**。 这是有用的如果你想要显示的不会显示在其他 SharePoint 组件**服务器资源管理器**默认情况下。 有关详细信息，请参阅[扩展服务器资源管理器中的 SharePoint 连接节点](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。  
  
 若要添加自定义节点，首先创建定义新节点的类。 然后创建将节点添加为现有节点的子节点的扩展。  
  
### <a name="to-define-the-new-node"></a>若要定义新的节点  
  
1.  创建类库项目。  
  
2.  添加对下列程序集的引用：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
    -   System.Drawing  
  
3.  创建实现 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> 接口的类。  
  
4.  将以下属性添加到类：  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>。 此属性使 Visual Studio 发现和加载你<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>实现。 传递<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>给特性构造函数的类型。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>。 在节点定义中，此属性指定新节点的字符串标识符。 我们建议你使用格式*公司名称*。*节点名称*若要确保所有节点都具有唯一标识符。  
  
5.  实现中<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A>方法，使用成员*typeDefinition*参数来配置新节点的行为。 此参数是<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>提供对中定义的事件的访问的对象<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents>接口。  
  
     下面的代码示例演示如何定义一个新的节点。 此示例假定你的项目包含名为 CustomChildNodeIcon 作为嵌入资源的图标。  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#6)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#6)]  
  
### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>若要将新节点添加为现有节点的子节点  
  
1.  在与你的节点定义相同的项目，创建一个类以实现<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>接口。  
  
2.  添加<xref:System.ComponentModel.Composition.ExportAttribute>到类属性。 此属性使 Visual Studio 发现和加载你<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>实现。 传递<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>给特性构造函数的类型。  
  
3.  添加<xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>到类属性。 在节点扩展中，此属性指定你想要扩展的节点的类型的字符串标识符。  
  
     若要指定由 Visual Studio 提供的内置节点类型，请将下面的枚举值之一传递给特性构造函数：  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>： 使用这些值来指定站点连接节点 （节点显示站点 Url），站点中的所有其他父节点或节点，**服务器资源管理器**。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>： 使用这些值可指定其中一个内置节点表示 SharePoint 站点，如表示列表、 字段或内容类型的节点上的单个组件。  
  
4.  实现中<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A>方法时，句柄<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>事件<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>参数。  
  
5.  在<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>事件处理程序，将新节点添加到的子节点集合<xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A>公开的事件自变量参数的对象。  
  
     下面的代码示例演示如何将新节点添加为 SharePoint 站点中节点的子**服务器资源管理器**。  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#7)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#7)]  
  
## <a name="complete-example"></a>完整的示例  
 下面的代码示例提供了完整的代码定义一个简单的节点并将其添加为 SharePoint 站点中节点的子**服务器资源管理器**。  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#5)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#5)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例假定你的项目包含名为 CustomChildNodeIcon 作为嵌入资源的图标。 此示例还需要对以下程序集的引用：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
-   System.Drawing  
  
## <a name="deploying-the-extension"></a>部署扩展  
 若要部署**服务器资源管理器**扩展，创建[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]扩展 (VSIX) 包的程序集和你想要随此扩展分发的任何其他文件。 有关详细信息，请参阅[部署 Visual Studio 中的 SharePoint 工具扩展](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另请参阅  
 [扩展服务器资源管理器中的 SharePoint 连接节点](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [如何： 扩展服务器资源管理器中的 SharePoint 节点](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [演练：扩展服务器资源管理器以显示 Web 部件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  