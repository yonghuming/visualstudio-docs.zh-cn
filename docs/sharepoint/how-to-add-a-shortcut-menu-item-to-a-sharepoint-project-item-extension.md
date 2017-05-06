---
title: "How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension"
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
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: d00513a6-d66d-4fbe-9efa-ef3b08c9a73a
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension
  可以通过使用项目项扩展向现有 SharePoint 项目项中添加快捷菜单项。  当用户在**“解决方案资源管理器”**中右击某个项目项时，将会显示相应的菜单项。  
  
 下面的步骤假定您已创建了一个项目项扩展。  有关更多信息，请参见[How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。  
  
### 在项目项扩展中添加快捷菜单项  
  
1.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 实现的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> 方法中，处理 *projectItemType* 参数的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> 事件。  
  
2.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> 事件的事件处理程序中，将新的 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> 对象添加到事件实参参数的 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> 或 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> 集合中。  
  
3.  在新的 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> 对象的 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> 事件处理程序中，执行您希望在用户单击快捷菜单项时执行的任务。  
  
## 示例  
 下面的代码示例演示如何将快捷菜单项添加到事件接收器项目项中。  当用户在**“解决方案资源管理器”**中右击该项目项并单击**“Write Message to Output Window”（向输出窗口写入消息）**菜单项时，Visual Studio 将在**“输出”**窗口中显示一条消息。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemextensionmenu.vb#1)]  
  
 此示例使用 SharePoint 项目服务将消息写入到**“输出”**窗口。  有关更多信息，请参见[Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)。  
  
## 编译代码  
 此示例需要引用了下列程序集的类库项目：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 部署扩展  
 若要部署扩展，请为要随此扩展分发的程序集和任何其他文件创建 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 扩展 \(VSIX\) 包。  有关更多信息，请参见[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 请参阅  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  