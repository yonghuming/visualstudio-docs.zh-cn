---
title: "使用服务器资源管理器浏览 SharePoint 连接"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.SharePointExplorer.SharePointConnection"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint 连接 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 浏览 SharePoint 站点"
  - "Visual Studio 中的 SharePoint 开发, SharePoint 连接"
ms.assetid: b3b1d97b-e990-414c-8ba5-3fd1b463fbef
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# 使用服务器资源管理器浏览 SharePoint 连接
  您现在可以在 **服务器资源管理器**中浏览本地 SharePoint 连接。  利用此项功能，您可以导航位于系统中的 SharePoint 网站的组件。  SharePoint 网站组件（例如，列表定义和内容类型）显示在“服务器资源管理器”窗口的树视图中一个名为“SharePoint 连接”的节点中。  若要显示**服务器资源管理器**，请在菜单栏上选择**视图**，**服务器资源管理器**。  除了显示 SharePoint 网站组件以外，通过使用快捷菜单命令，您还可以移除项、查看它们的属性或刷新树视图。  
  
> [!IMPORTANT]  
>  若要浏览 SharePoint 网站，您必须是 SharePoint 网站集上的管理员，并且必须以本地计算机管理员用户身份运行 Visual Studio。  否则，**服务器资源管理器**中将显示该网站，但您不能展开其节点。  若要验证您是否是网站集的管理员，在web浏览器中打开网站，打开 **网站操作** 菜单，选择 **网站权限**，然后在 **Permissions:工作组网站**页，在功能区中选择 **管理** 组，选择 **网站集管理员**命令 。  如果您是网站集管理员，则您的名称将会出现在文本框中。  如果 **网站集管理员** 命令的效果不能在功能区的管理组中出现，则您不是网站集的管理员，而且，您必须从站点管理员获取适当的权限。  
  
## 服务器资源管理器节点  
 SharePoint 网站的每个组件均由**服务器资源管理器**树视图中的**SharePoint连接**下的一个节点表示。  例如，默认 SharePoint 网站包括一个名为“讨论”的内容类型，它表示 SharePoint 网站的**“讨论”**页中显示的一个讨论类型。  “讨论”内容类型包含若干个字段。  若要在 **服务器资源管理器**中查看这些字段，请展开**内容类型**节点，再展开**讨论**节点。  该节点之下是几个字段节点，例如，“正文”、“讨论主题”和“标题”。  
  
## 节点快捷菜单命令  
 每个节点都有一个可通过右击节点或选择该连接并选择 Shift\+F10 键访问的快捷菜单。  节点命令可能包括：  
  
|命令名|说明|  
|---------|--------|  
|刷新|更新树视图，以反映节点自上次显示以来可能发生的任何更改。|  
|Delete|从树视图中移除选定的节点。 **Note:**  将只对在**“SharePoint 连接”**节点下列出的 SharePoint 连接启用此命令。|  
|属性|在**“属性”**窗口中显示选定节点的可用属性。  所有属性都是只读的，并不是每个节点都关联有属性。|  
|添加连接|允许您指定要浏览的 SharePoint 网站。  在**“SharePoint 连接”**节点和子网站节点上可用。|  
|在浏览器中查看|在 Web 浏览器中显示选定列表。  此命令对**“列表和库”**中包含的**“列表”**节点下的某些列表可用。|  
  
## 相关主题  
  
|标题|说明|  
|--------|--------|  
|[如何：添加或移除 SharePoint 连接](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|描述将新的 SharePoint 网站添加到**“服务器资源管理器”**的**“SharePoint 连接”**节点中所需的步骤。|  
  
## 请参阅  
 [服务器资源管理器](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d)   
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  