---
title: "如何： 检索 SharePoint 项目服务 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: SharePoint project service
ms.assetid: 3d8b7adf-2603-4247-9b61-6326a1dd0dec
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b5ecc739da7cc3aa78a5c175ae323f5cd2447d40
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>如何：检索 SharePoint 项目服务
  你可以访问以下类型的解决方案中的 SharePoint 项目服务：  
  
-   SharePoint 项目系统，如项目扩展、 项目项扩展或项目项类型定义的扩展。 有关这些类型的扩展的详细信息，请参阅[扩展 SharePoint 项目系统](../sharepoint/extending-the-sharepoint-project-system.md)。  
  
-   扩展**SharePoint 连接**中的节点**服务器资源管理器**。 有关这些类型的扩展的详细信息，请参阅[扩展服务器资源管理器中的 SharePoint 连接节点](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。  
  
-   另一种 Visual Studio 扩展，如 VSPackage。  
  
## <a name="retrieving-the-service-in-project-system-extensions"></a>检索项目系统扩展中的服务  
 在 SharePoint 项目系统的任何扩展中，你可以通过访问项目服务<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A>属性<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>对象。  
  
 您还可以通过使用以下过程来检索该项目服务。  
  
#### <a name="to-retrieve-the-service-in-a-project-extension"></a>若要检索项目扩展中的服务  
  
1.  实现中<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>接口，找到<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>方法。  
  
2.  使用*projectService*参数来访问服务。  
  
     下面的代码示例演示如何使用该项目服务写入到消息**输出**窗口和**错误列表**简单项目扩展中的窗口。  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]  
  
     有关创建项目扩展的详细信息，请参阅[如何： 创建 SharePoint 项目扩展](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。  
  
#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>若要检索项目项扩展中的服务  
  
1.  实现中<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>接口，找到<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>方法。  
  
2.  使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A>属性*projectItemType*参数来检索服务。  
  
     下面的代码示例演示如何使用该项目服务写入到消息**输出**窗口和**错误列表**窗口中的简单的扩展名**列表定义**项目项。  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]  
  
     有关创建项目项扩展的详细信息，请参阅[如何： 创建 SharePoint 项目项扩展](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。  
  
#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>若要检索的项目项类型定义中的服务  
  
1.  实现中<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>接口，找到<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>方法。  
  
2.  使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A>属性*typeDefinition*参数来检索服务。  
  
     下面的代码示例演示如何使用该项目服务写入到消息**输出**窗口和**错误列表**简单项目项类型定义中的窗口。  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]  
  
     有关定义项目项类型的详细信息，请参阅[如何： 定义 SharePoint 项目项类型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。  
  
## <a name="retrieving-the-service-in-server-explorer-extensions"></a>检索服务器资源管理器扩展中的服务  
 中的扩展**SharePoint 连接**中的节点**服务器资源管理器**，你可以通过访问项目服务<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A>属性<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>对象。  
  
#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>若要检索的服务器资源管理器扩展中的服务  
  
1.  获取<xref:System.IServiceProvider>对象<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A>属性<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>扩展中的对象。  
  
2.  使用<xref:System.IServiceProvider.GetService%2A>方法来请求<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>对象。  
  
     下面的代码示例演示如何使用该项目服务写入到消息**输出**窗口和**错误列表**从通过扩展添加到列表中的节点的快捷菜单窗口**服务器资源管理器**。  
  
     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]  
  
     有关扩展的详细信息**SharePoint 连接**中的节点**服务器资源管理器**，请参阅[如何： 扩展服务器资源管理器中的 SharePoint 节点](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。  
  
## <a name="retrieving-the-service-in-other-visual-studio-extensions"></a>检索其他 Visual Studio 扩展中的服务  
 你可以检索该项目服务，在 VSPackage 中或在有权访问任何 Visual Studio 扩展中<xref:EnvDTE80.DTE2>自动化对象模型，如实现项目模板向导中的对象<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>接口。  
  
 在 VSPackage，你可以请求<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>对象通过使用以下方法之一：  
  
-   <xref:System.IServiceProvider.GetService%2A>方法的派生自托管的 VSPackage<xref:Microsoft.VisualStudio.Shell.Package>类。 有关详细信息，请参阅[如何： 获取服务](../extensibility/how-to-get-a-service.md)。  
  
-   静态<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>方法。 有关详细信息，请参阅[使用 GetGlobalService](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice)。  
  
 在 Visual Studio 扩展有权访问<xref:EnvDTE80.DTE2>对象，你可以请求<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>通过使用对象<xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>方法<xref:Microsoft.VisualStudio.Shell.ServiceProvider>对象。 有关详细信息，请参阅[从 DTE 对象获取服务](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object)。  
  
## <a name="see-also"></a>另请参阅  
 [使用 SharePoint 项目服务](../sharepoint/using-the-sharepoint-project-service.md)   
 [如何： 将获得的服务](../extensibility/how-to-get-a-service.md)   
 [如何：使用向导来处理项目模板](../extensibility/how-to-use-wizards-with-project-templates.md)  
  
  