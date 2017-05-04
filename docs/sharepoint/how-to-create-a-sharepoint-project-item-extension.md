---
title: "How to: Create a SharePoint Project Item Extension | Microsoft Docs"
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
ms.assetid: 163738b9-e25a-49c9-8f33-4b57a2da6b07
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# How to: Create a SharePoint Project Item Extension
  当您希望向 Visual Studio 中已安装的 SharePoint 项目项添加功能时，请创建项目项扩展。  有关更多信息，请参见[Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)。  
  
### 创建项目项扩展  
  
1.  创建一个类库项目。  
  
2.  添加对下列程序集的引用：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  创建一个实现 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 接口的类。  
  
4.  向该类添加下列特性：  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>.  此特性使 Visual Studio 能够发现和加载您的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 实现。  将 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 类型传递给特性构造函数。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  在项目项扩展中，此特性标识要扩展的项目项。  将项目项的 ID 传递给特性构造函数。  有关项目项的 ID 的列表包含在 Visual Studio，请参见 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)。  
  
5.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> 方法的实现中，使用 *projectItemType* 参数的成员来定义扩展的行为。  此参数是一个 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> 对象，它提供对 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 和 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> 接口中定义的事件的访问。  若要访问要扩展的项目项类型的特定实例，请处理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 事件（如 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> 和 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>）。  
  
## 示例  
 下面的代码示例演示如何为事件接收器项目项创建一个简单的扩展。  每当用户向 SharePoint 项目添加事件接收器项目项时，此扩展就会向**“输出”**窗口和**“错误列表”**窗口中写入一条消息。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/projectitemextension.vb#1)]  
  
 此示例使用 SharePoint 项目服务将消息写入到**“输出”**窗口和**“错误列表”**窗口。  有关更多信息，请参见[Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)。  
  
## 编译代码  
 此示例需要对以下程序集的引用：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 部署扩展  
 若要部署扩展，请为要随此扩展分发的程序集和任何其他文件创建 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 扩展 \(VSIX\) 包。  有关更多信息，请参见[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 请参阅  
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  