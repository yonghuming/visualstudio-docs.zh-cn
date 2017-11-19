---
title: "扩展 Visual Studio 中的 SharePoint 工具 |Microsoft 文档"
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
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
ms.assetid: 084cf4bf-aaba-4277-8032-448f2cb2a124
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b78f90df8b6e46774310bd4a8cf218fbcbc7a18b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="extending-the-sharepoint-tools-in-visual-studio"></a>扩展 Visual Studio 中的 SharePoint 工具
  Visual Studio 中的 SharePoint 工具满足许多应用程序开发方案的要求。 但是，你可能会发现它们不提供你或其他开发人员需要的功能的情况。 在这些情况下，你可以扩展 SharePoint 工具以创建所需的功能。  
  
## <a name="how-to-extend-the-sharepoint-tools"></a>如何扩展 SharePoint 工具  
 你可以扩展 SharePoint 项目系统和**SharePoint 连接**中的节点**服务器资源管理器**窗口。  
  
### <a name="extending-the-sharepoint-project-system"></a>扩展 SharePoint 项目系统  
 Visual Studio 包含一组项目模板和项模板可用于创建 SharePoint 解决方案。 例如，有的事件接收器、 列表定义、 工作流和 Web 部件的模板。 但是，你还可以定义自己的用于创建 SharePoint 组件，如字段或自定义操作的 SharePoint 项目项类型。 你还可以创建用于在 Visual Studio 中，已安装的 SharePoint 项目项类型的扩展，并且可以创建用于 SharePoint 项目扩展。  
  
 有关详细信息，请参阅[扩展 SharePoint 项目系统](../sharepoint/extending-the-sharepoint-project-system.md)。  
  
### <a name="extending-the-sharepoint-connections-node-in-server-explorer"></a>扩展服务器资源管理器中的“SharePoint 连接”节点  
 在 Visual Studio 中，你可以使用**SharePoint 连接**中的节点**服务器资源管理器**窗口，以在分层树视图中查看许多的组件的一个或多个本地 SharePoint 站点。 你还可以扩展**SharePoint 连接**节点通过以下方式：  
  
-   通过添加你自己的节点。 这是你想要显示的默认不显示的 SharePoint 网站组件的情况下很有用。  
  
-   通过扩展现有节点。 例如，可以将新的子节点添加到现有节点中，或者可以向节点添加快捷菜单项和开发人员单击菜单项时执行任务。  
  
 有关详细信息，请参阅[扩展服务器资源管理器中的 SharePoint 连接节点](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。  
  
## <a name="development-computer-requirements"></a>开发计算机要求  
 若要创建 SharePoint 工具扩展，你的开发计算机必须满足在 Visual Studio 中创建 SharePoint 解决方案的相同要求。 有关详细信息，请参阅[有关开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
 我们还建议你安装[!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。 SDK 包括项目模板和可用于扩展 Visual Studio 的工具。 具体而言，SDK 包含可用于轻松地创建 Visual Studio 扩展 (VSIX) 包的项目模板。 VSIX 包是部署 Visual Studio 扩展 Visual Studio 中的首选的方法。 必须使用 VSIX 包来部署所有 SharePoint 工具扩展。 所有本文档中的演练假设你有[!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]安装。  
  
 若要安装 Visual Studio SDK，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。 有关 Visual Studio 扩展的详细信息，请参阅[开始开发 Visual Studio 扩展到](../extensibility/starting-to-develop-visual-studio-extensions.md)。  
  
## <a name="see-also"></a>另请参阅  
 [概述的编程模型的 SharePoint 工具扩展](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [扩展 SharePoint 项目系统](../sharepoint/extending-the-sharepoint-project-system.md)   
 [扩展服务器资源管理器中的 SharePoint 连接节点](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [SharePoint 工具扩展的编程概念和功能](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [引用 &#40;SharePoint 工具扩展 &#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)   
 [调试 Visual Studio 中的 SharePoint 工具扩展](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)   
 [在 Visual Studio 中部署 SharePoint 工具扩展](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  