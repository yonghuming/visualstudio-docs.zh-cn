---
title: "How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type"
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
  - "SharePoint project items, defining your own types"
  - "project items [SharePoint development in Visual Studio], defining your own types"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: f6ec47a7-e7d9-4e26-810b-77943a1ab04c
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type
  在定义自定义 SharePoint 项目项类型时，可向项目项中添加快捷菜单项。  当用户在**“解决方案资源管理器”**中右击某个项目项时，将会显示相应的菜单项。  
  
 下面的步骤假定您已定义了自己的 SharePoint 项目项类型。  有关更多信息，请参见[How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。  
  
### 向自定义项目项类型中添加快捷菜单项  
  
1.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 实现的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> 方法中，处理 *projectItemTypeDefinition* 参数的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> 事件。  
  
2.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> 事件的事件处理程序中，将新的 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> 对象添加到事件实参参数的 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> 或 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> 集合中。  
  
3.  在新 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> 对象的 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> 事件处理程序中，执行要执行的任务用户何时选择您的快捷菜单项。  
  
## 示例  
 下面的代码示例演示如何将上下文菜单项添加到自定义项目项类型中。  当用户从打开项目项的快捷菜单在 **解决方案资源管理器** 并选择 **将消息写入输出窗口** 菜单项时，Visual Studio 将显示在 **输出** 窗口的消息。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypemenu.vb#4)]  
  
 此示例使用 SharePoint 项目服务将消息写入到**“输出”**窗口。  有关更多信息，请参见[Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)。  
  
## 编译代码  
 此示例需要引用了下列程序集的类库项目：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 部署项目项  
 若要使其他开发人员能够使用您的项目项，请创建一个项目模板或项目项模板。  有关更多信息，请参见[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
 若要部署项目项，请为要随此项目项分发的程序集、模板及任何其他文件创建 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 扩展 \(VSIX\) 包。  有关更多信息，请参见[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 请参阅  
 [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  