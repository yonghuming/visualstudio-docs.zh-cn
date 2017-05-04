---
title: "How to: Add a Shortcut Menu Item to SharePoint Projects | Microsoft Docs"
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
  - "projects [SharePoint development in Visual Studio], extending"
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint projects, extending"
ms.assetid: bb251fe9-f1bf-4ddd-9359-4b7f78fbd50f
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# How to: Add a Shortcut Menu Item to SharePoint Projects
  可以向任何 SharePoint 项目中添加快捷菜单项。  当用户在**“解决方案资源管理器”**中右击某个项目节点时，将出现该菜单项。  
  
 下面的步骤假定您已创建了一个项目扩展。  有关更多信息，请参见[How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。  
  
### 向 SharePoint 项目中添加快捷菜单项  
  
1.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 实现的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> 方法中，处理 *projectService* 参数的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> 事件。  
  
2.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> 事件的事件处理程序中，将新的 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> 对象添加到事件实参参数的 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> 或 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> 集合中。  
  
3.  在新的 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> 对象的 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> 事件处理程序中，执行您希望在用户单击快捷菜单项时执行的任务。  
  
## 示例  
 下面的代码示例演示如何向**“解决方案资源管理器”**中的 SharePoint 项目节点添加快捷菜单项。  当用户右击项目节点并单击**“Write Message to Output Window”（向输出窗口写入消息）**菜单项时，Visual Studio 将在 **“输出”**窗口中显示一条消息。  此示例使用 SharePoint 项目服务来显示消息。  有关更多信息，请参见[Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)。  
  
 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.menu/cs/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.menu/vb/extension/projectitemextensionmenu.vb#1)]  
  
## 编译代码  
 此示例需要引用了下列程序集的类库项目：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 部署扩展  
 若要部署扩展，请为要随此扩展分发的程序集和任何其他文件创建 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 扩展 \(VSIX\) 包。  有关更多信息，请参见[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 请参阅  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)  
  
  