---
title: "如何： 在服务器资源管理器中的内置 SharePoint 节点获取数据 |Microsoft 文档"
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
ms.assetid: 86d04e0a-c114-427e-9945-da5fa339fda4
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b61003516d7551c99f6e265ca2eeced9226958df
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>如何：为服务器资源管理器中的内置 SharePoint 节点获取数据
  在每个内置 SharePoint 节点**服务器资源管理器**，则可以在该节点表示的基础 SharePoint 组件中获取数据。 有关详细信息，请参阅[扩展服务器资源管理器中的 SharePoint 连接节点](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。  
  
## <a name="example"></a>示例  
 下面的代码示例演示如何获取基础列表节点表示中的 SharePoint 列表数据**服务器资源管理器**。 默认情况下，列表节点具有**用浏览器查看**可以单击以打开列表，在 Web 浏览器的上下文菜单项。 此示例通过添加扩展列表节点**Visual Studio 中的视图**直接在 Visual Studio 中打开列出的上下文菜单项。 代码访问节点获取要在 Visual Studio 中打开的列表的 URL 的列表数据。  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]  
  
 此示例使用 SharePoint 项目服务来获取<xref:EnvDTE.DTE>Visual Studio 中列出了用于打开的对象。 SharePoint 项目服务有关的详细信息，请参阅[使用 SharePoint 项目服务](../sharepoint/using-the-sharepoint-project-service.md)。  
  
 有关创建扩展的 SharePoint 节点的基本任务的详细信息，请参阅[如何： 扩展服务器资源管理器中的 SharePoint 节点](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要引用以下程序集：  
  
-   EnvDTE  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>部署扩展  
 若要部署**服务器资源管理器**扩展，创建[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]扩展 (VSIX) 包的程序集和你想要随此扩展分发的任何其他文件。 有关详细信息，请参阅[部署 Visual Studio 中的 SharePoint 工具扩展](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另请参阅  
 [扩展服务器资源管理器中的 SharePoint 连接节点](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [如何： 扩展服务器资源管理器中的 SharePoint 节点](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [使用 SharePoint 项目服务](../sharepoint/using-the-sharepoint-project-service.md)   
 [在 Visual Studio 中部署 SharePoint 工具扩展](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  