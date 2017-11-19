---
title: "使用服务器资源管理器浏览 SharePoint 连接 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.SharePointExplorer.SharePointConnection
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
ms.assetid: b3b1d97b-e990-414c-8ba5-3fd1b463fbef
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9b8f75dd12e0684edd4260e796540523a2c7d08d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="browsing-sharepoint-connections-using-server-explorer"></a>使用服务器资源管理器浏览 SharePoint 连接
  你现在可以浏览本地 SharePoint 连接中的**服务器资源管理器**。 通过使用这种方法，您可以在系统上浏览 SharePoint 网站的组件。 SharePoint 网站组件，例如列表定义和内容类型，显示的名为一个节点**SharePoint 连接**的树视图中**服务器资源管理器**。 若要显示**服务器资源管理器**，在菜单栏上，选择**视图**，**服务器资源管理器**。 除了显示 SharePoint 网站组件以外，通过使用快捷菜单命令，你还可以移除项、查看它们的属性或刷新树视图。  
  
> [!IMPORTANT]  
>  若要浏览 SharePoint 网站，您必须是 SharePoint 网站集的管理员，并且必须以本地计算机管理员身份运行 Visual Studio。 否则，站点会显示在**服务器资源管理器**，但不能展开其节点。 若要验证是否是站点集的管理员，打开站点，在 web 浏览器中，打开**站点操作**菜单上，选择**站点权限**，然后在**权限： 团队站点**页上，选择**网站集管理员**命令**管理**组功能区上。 如果您是站点集管理员，你的名称将显示在文本框中。 如果**网站集管理员**命令未显示在功能区上的管理组不是找不到站点的管理员，你必须从站点管理员处获取适当的权限。  
  
## <a name="server-explorer-nodes"></a>服务器资源管理器节点  
 中的节点表示 SharePoint 站点的每个组件**服务器资源管理器**树视图下的**SharePoint 连接**。 例如，默认 SharePoint 站点包括一个名讨论，表示显示中的讨论类型的内容类型**讨论**在 SharePoint 站点的页面。 讨论内容类型包含多个字段。 若要查看中的这些字段**服务器资源管理器**，展开**内容类型**节点，然后**讨论**节点。 该节点之下是字段中的多个节点，如正文、 讨论使用者和标题。  
  
## <a name="node-shortcut-menu-commands"></a>节点的快捷菜单命令  
 每个节点都有一个快捷菜单，可通过右击该节点或选择该节点并选择 Shift+F10 来访问快捷菜单。 节点命令可能包括：  
  
|命令名：|描述|  
|------------------|-----------------|  
|刷新|更新以反映该节点已显示的上次可能已发生的任何更改的树视图。|  
|删除|从树视图中删除所选的节点。 **注意：**此命令启用仅在下列出的 SharePoint 连接上**SharePoint 连接**节点。|  
|属性|显示在所选节点的可用属性**属性**窗口。 属性是只读的并不是每个节点具有与之关联的属性。|  
|添加连接|使用此选项可以指定你想要浏览 SharePoint 站点。 可在上找到**SharePoint 连接**节点和子站点节点。|  
|在浏览器中查看|在 Web 浏览器中显示选定的列表。 此命令是在下的某些列表上可用**列出**节点中包含的**列表和库**。|  
  
## <a name="related-topics"></a>相关主题  
  
|标题|描述|  
|-----------|-----------------|  
|[如何：添加或删除 SharePoint 连接](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|描述所需的添加到新的 SharePoint 站点的步骤**SharePoint 连接**中的节点**服务器资源管理器**。|  
  
## <a name="see-also"></a>另请参阅  
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  