---
title: "How to: Create a SharePoint Project Extension | Microsoft Docs"
ms.custom: ""
ms.date: "04/28/2017"
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
ms.assetid: ceecb9cb-4a5d-44c9-992f-9624737ac996
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# How to: Create a SharePoint Project Extension
  当您希望向在 Visual Studio 中打开的任何 SharePoint 项目添加功能时，可创建一个项目扩展。  有关更多信息，请参见[Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)。  
  
### 创建项目扩展  
  
1.  创建一个类库项目。  
  
2.  添加对下列程序集的引用：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  创建一个实现 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 接口的类。  
  
4.  将 <xref:System.ComponentModel.Composition.ExportAttribute> 添加到该类中。  此特性使 Visual Studio 能够发现并加载您的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 实现。  将 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 类型传递给特性构造函数。  
  
5.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> 方法的实现中，使用 *projectService* 参数的成员来定义扩展的行为。  此参数是一个 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 对象，它提供对 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> 接口中定义的事件的访问。  
  
## 示例  
 下面的代码示例演示如何创建一个简单的项目扩展，此扩展将处理由 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> 接口定义的大多数 SharePoint 项目事件。  若要测试代码，请在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中创建一个 SharePoint 项目，然后向解决方案中添加更多项目，更改项目属性值，或者删除或排除项目。  该扩展通过在**“输出”**窗口和**“错误列表”**窗口中写入消息，通知您有关事件。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/projectextension.cs#3)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/projectextension.vb#3)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/savedatatoprojectfile.vb#3)]  
  
 此示例使用 SharePoint 项目服务将消息写入到**“输出”**窗口和**“错误列表”**窗口。  有关更多信息，请参见[Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)。  
  
 有关演示如何处理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> 和 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> 事件的示例，请参见[How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)和[How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)。  
  
## 编译代码  
 此示例需要对以下程序集的引用：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 部署扩展  
 若要部署扩展，请为要随此扩展分发的程序集和任何其他文件创建 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 扩展 \(VSIX\) 包。  有关更多信息，请参见[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 请参阅  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)  
  
  