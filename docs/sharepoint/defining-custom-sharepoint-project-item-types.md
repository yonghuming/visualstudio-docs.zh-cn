---
title: "Defining Custom SharePoint Project Item Types | Microsoft Docs"
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
ms.assetid: be300c24-fd1b-4fc7-a4e9-a5df1d81d3fc
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Defining Custom SharePoint Project Item Types
  当您希望创建新类型的 SharePoint 项目项时，请定义新的 SharePoint 项目项类型。  例如， Visual Studio 不包含用于向 SharePoint 网站添加字段或自定义操作的 SharePoint 项目项。  可以定义您自己的 SharePoint 项目项类型，以创建字段、自定义操作或其他类型的 SharePoint 组件。  
  
## 用于定义 SharePoint 项目项类型的任务  
 若要定义自定义项目项类型，请生成实现 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 接口的 Visual Studio 扩展程序集。  有关更多信息，请参见[How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。  
  
 在定义自定义项目项类型时，还可以向项目项中添加以下功能：  
  
-   向项目项中添加快捷菜单项。  菜单项会在您打开项目项的快捷菜单在 **解决方案资源管理器** 通过右击项目项或通过选择然后选择 SHIFT \+ F10 键。  有关更多信息，请参见[How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)。  
  
-   向项目项中添加自定义属性。  当您在中选择 **解决方案资源管理器**时，的项目项属性出现在 **属性** 窗口。  有关更多信息，请参见[How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)。  
  
 若要使其他开发人员可以在 Visual Studio 中使用您的项目项，请创建一个 .spdata 文件，并创建一个与该项目项关联的项模板或项目模板。  有关更多信息，请参见[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
## 了解项目项类型与项目项实例之间的关系  
 如果定义了 SharePoint 项目项类型，则在向 SharePoint 项目中添加关联类型的项目项时，Visual Studio 会加载您的扩展。  例如，如果您定义了一个新的**“自定义操作”**项目项类型，则在用户向项目中添加**“自定义操作”**项目项时，Visual Studio 会加载您的扩展。  Visual Studio 会将扩展的同一个实例用于关联项目项类型的所有实例。  在前面的示例中，如果用户向项目中添加另一个**“自定义操作”**项目项，则会使用同一个扩展实例来自定义第二个项目项。  
  
 若要访问项目项类型的特定实例，请在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> 方法的实现中处理 *projectItemTypeDefinition* 参数的一个 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 事件。  例如，若要确定自定义类型的项目项添加到项目中的时间，请处理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> 事件。  有关更多信息，请参见[How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。  
  
## 请参阅  
 [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [演练：使用项目模板创建网站栏项目项（第 1 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [演练：使用项目模板创建网站栏项目项（第 2 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  