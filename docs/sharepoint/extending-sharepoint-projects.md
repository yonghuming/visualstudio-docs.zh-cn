---
title: "Extending SharePoint Projects | Microsoft Docs"
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
ms.assetid: 4643012b-6e6c-4b7c-bb92-b04b34f6c715
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Extending SharePoint Projects
  当您希望自定义 SharePoint 项目的项目级功能时，请创建项目扩展。  例如，您可以添加自定义项目属性，或响应用户在 Visual Studio 中开发 SharePoint 解决方案时引发的项目级事件。  
  
## 创建项目扩展  
 若要扩展项目项，请生成实现 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 接口的 Visual Studio 扩展程序集。  有关更多信息，请参见[How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。  
  
 在创建项目扩展时，您还可以向 SharePoint 项目中添加以下功能：  
  
-   添加快捷菜单项。  菜单项会在您通过右击节点或选择然后选择 SHIFT \+ F10 键打开一个 SharePoint 项目节点的快捷菜单在 **解决方案资源管理器**。  有关更多信息，请参见[How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)。  
  
-   添加自定义属性。  当您在中选择 **解决方案资源管理器**时，的 SharePoint 项目属性出现在 **属性** 窗口。  有关更多信息，请参见[How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)。  
  
 有关演示如何创建、部署和测试项目扩展的演练，请参见[Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)。  
  
## 了解项目扩展与项目实例之间的关系  
 创建项目扩展后，当在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中打开任何类型的 SharePoint 项目时，此扩展都会加载。[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 包含若干个 SharePoint 项目模板，如列表定义、内容类型和事件接收器。  但只有一个 SharePoint 项目类型。  **“新建项目”**对话框中显示的项目类型只不过是将一个或多个 SharePoint 项目项绑定在一起的模板。  由于只存在一个 SharePoint 项目类型，因此为一个项目创建的扩展将适用于所有 SharePoint 项目。  例如，您无法创建一个只适用于**“内容类型”**项目的扩展。  
  
 若要访问特定项目实例，请在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> 方法的实现中处理 *projectService* 参数的一个 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> 事件。  例如，若要确定 SharePoint 项目添加到解决方案中的时间，请处理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> 事件。  有关更多信息，请参见[How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。  
  
## 请参阅  
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  