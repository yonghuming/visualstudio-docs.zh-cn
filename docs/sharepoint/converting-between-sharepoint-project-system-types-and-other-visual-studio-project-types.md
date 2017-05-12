---
title: "Converting Between SharePoint Project System Types and Other Visual Studio Project Types | Microsoft Docs"
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
  - "SharePoint project service"
ms.assetid: ad5d8ab2-1659-4e6a-8783-47e0dad44b11
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Converting Between SharePoint Project System Types and Other Visual Studio Project Types
  在某些情况下，您可能拥有 SharePoint 项目系统中的一个对象，希望使用 Visual Studio 自动化对象模型或集成对象模型中相应对象的功能。或者，您可能拥有 Visual Studio 自动化对象模型或集成对象模型中的对象，希望使用 SharePoint 项目系统中相应对象的功能。  在上述情况中，可以使用 SharePoint 项目服务的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> 方法将对象转换为不同的对象模型。  
  
 例如，您可能拥有一个 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 对象，但希望使用仅对 <xref:EnvDTE.Project> 或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> 对象可用的方法。  在此情形中，您可以使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> 方法，将 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 转换为 <xref:EnvDTE.Project> 或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>。  
  
 有关 Visual Studio 自动化对象模型和 Visual Studio 集成对象模型的更多信息，请参见[Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)。  
  
## 转换的类型  
 下表列出了可利用此方法在 SharePoint 项目系统和其他 Visual Studio 对象模型之间进行转换的类型。  
  
|SharePoint 项目系统类型|自动化对象模型和集成对象模型中的对应类型|  
|-----------------------|--------------------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> 或<br /><br /> Visual Studio 集成对象模型中由项目的基础 COM 对象实现的任何接口。  这些接口包括 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>（或派生接口）和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>。  有关由项目实现的主接口的列表，请参见[项目模型核心组件](../extensibility/internals/project-model-core-components.md)。|  
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> 或<br /><br /> 一个 <xref:System.UInt32> 值，也称作 VSITEMID，用于在包含某项目成员的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 中标识该项目成员。  此值可以传递给某些 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 方法的 *itemid* 参数。|  
  
## 示例  
 下面的代码示例演示如何使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> 方法，将 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 对象转换为 <xref:EnvDTE.Project>。  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/cs/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/vb/connect.vb#2)]  
  
 此示例需要：  
  
-   具有对 EnvDTE.dll 程序集的引用的 SharePoint 项目系统的扩展。  有关更多信息，请参见[Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)。  
  
-   用于注册 `projectService_ProjectAdded` 方法以处理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 对象的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> 事件的代码。  有关示例，请参见[How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。  
  
## 请参阅  
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  