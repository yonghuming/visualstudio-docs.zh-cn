---
title: "How to: Define a SharePoint Project Item Type"
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
ms.assetid: 18b56e7c-4efb-47a2-abfc-e9018ae38267
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# How to: Define a SharePoint Project Item Type
  当您希望创建自定义 SharePoint 项目项时，请定义项目项类型。  有关更多信息，请参见[Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)。  
  
### 定义项目项类型  
  
1.  创建一个类库项目。  
  
2.  添加对下列程序集的引用：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  创建一个实现 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 接口的类。  
  
4.  向该类添加下列特性：  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>.  此特性使 Visual Studio 能够发现和加载您的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 实现。  将 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 类型传递给特性构造函数。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  在项目项类型定义中，此特性指定新项目项的字符串标识符。  建议您使用“*公司名称*.*功能名称*”格式，以帮助确保所有项目项的名称都是唯一的。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>.  此特性指定要在**“解决方案资源管理器”**中为此项目项显示的图标。  此特性是可选的；如果未向类应用此特性，则 Visual Studio 将显示项目项的默认图标。  如果设置此特性，则应传递程序集中嵌入的图标或位图的完全限定名称。  
  
5.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> 方法的实现中，使用 *projectItemTypeDefinition* 参数的成员来定义项目项类型的行为。  此参数是一个 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> 对象，它提供对 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 和 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> 接口中定义的事件的访问。  若要访问项目项类型的特定实例，请处理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 事件（如 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> 和 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>）。  
  
## 示例  
 下面的代码示例演示如何定义一个简单的项目项类型。  当用户向项目中添加此类型的项目项时，此项目项类型就会向**“输出”**窗口和**“错误列表”**窗口中写入一条消息。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/projectitemtype.cs#2)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/projectitemtype.vb#2)]  
  
 此示例使用 SharePoint 项目服务将消息写入到**“输出”**窗口和**“错误列表”**窗口。  有关更多信息，请参见[Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)。  
  
## 编译代码  
 此示例需要对以下程序集的引用：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 部署项目项  
 若要使其他开发人员能够使用您的项目项，请创建一个项目模板或项目项模板。  有关更多信息，请参见[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
 若要部署项目项，请为要随此项目项分发的程序集、模板及任何其他文件创建 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 扩展 \(VSIX\) 包。  有关更多信息，请参见[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 请参阅  
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [演练：使用项目模板创建网站栏项目项（第 1 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)  
  
  