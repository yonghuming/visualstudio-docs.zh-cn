---
title: "How to: Retrieve the SharePoint Project Service | Microsoft Docs"
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
ms.assetid: 3d8b7adf-2603-4247-9b61-6326a1dd0dec
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# How to: Retrieve the SharePoint Project Service
  可以在以下类型的解决方案中访问 SharePoint 项目服务：  
  
-   SharePoint 项目系统的扩展，如项目扩展、项目项扩展或项目项类型定义。  有关这些扩展类型的更多信息，请参见[Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)。  
  
-   **“服务器资源管理器”**中的**“SharePoint 连接”**节点的扩展。  有关这些扩展类型的更多信息，请参见[Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。  
  
-   另一种类型的 Visual Studio 扩展，如外接程序或 VSPackage。  
  
## 在项目系统扩展中检索服务  
 在任何 SharePoint 项目系统扩展中，您都可以使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 对象的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> 属性来访问项目服务。  
  
 您也可以通过使用以下过程来检索项目服务。  
  
#### 在项目扩展中检索服务  
  
1.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 接口的实现中找到 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> 方法。  
  
2.  使用 *projectService* 参数访问服务。  
  
     下面的代码示例演示如何在一个简单的项目扩展中使用项目服务，将消息写入到**“输出”**窗口和**“错误列表”**窗口。  
  
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/cs/extension/extension.cs#1)]
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/vb/extension/extension.vb#1)]  
  
     有关创建项目扩展的更多信息，请参见[How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。  
  
#### 在项目项扩展中检索服务  
  
1.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 接口的实现中找到 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> 方法。  
  
2.  使用 *projectItemType* 参数的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> 属性检索服务。  
  
     下面的代码示例演示如何在**“列表定义”**项目项的一个简单扩展中使用项目服务，将消息写入到**“输出”**窗口和**“错误列表”**窗口。  
  
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/cs/extension/extension.cs#2)]
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/vb/extension/extension.vb#2)]  
  
     有关创建项目项扩展的更多信息，请参见[How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。  
  
#### 在项目项类型定义中检索服务  
  
1.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 接口的实现中找到 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> 方法。  
  
2.  使用 *typeDefinition* 参数的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> 属性检索服务。  
  
     下面的代码示例演示如何在一个简单的项目项类型定义中使用项目服务，将消息写入到**“输出”**窗口和**“错误列表”**窗口。  
  
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/cs/extension/extension.cs#3)]
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/vb/extension/extension.vb#3)]  
  
     有关定义项目项类型的更多信息，请参见[How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。  
  
## 在服务器资源管理器扩展中检索服务  
 在**“服务器资源管理器”**中的**“SharePoint 连接”**节点的扩展中，可以通过使用 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> 对象的 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> 属性来访问项目服务。  
  
#### 在服务器资源管理器扩展中检索服务  
  
1.  从扩展中的 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> 对象的 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> 属性获取 <xref:System.IServiceProvider> 对象。  
  
2.  使用 <xref:System.IServiceProvider.GetService%2A> 方法请求 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 对象。  
  
     下面的代码示例演示如何使用项目服务，通过扩展添加到**“服务器资源管理器”**中的列表节点的快捷菜单，将消息写入到**“输出”**窗口和**“错误列表”**窗口。  
  
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromspexplorerextensions/cs/extension/extension.cs#1)]
     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromspexplorerextensions/vb/extension/extension.vb#1)]  
  
     有关扩展**“服务器资源管理器”**中的**“SharePoint 连接”**节点的更多信息，请参见[How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。  
  
## 在其他 Visual Studio 扩展中检索项目服务  
 可以在 VSPackage 中检索项目服务，也可以在具有对自动化对象模型中的 <xref:EnvDTE80.DTE2> 对象的访问权的任何 Visual Studio 扩展（如外接程序或实现 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 接口的项目模板向导）中检索项目服务。  
  
 在 VSPackage 中，可以通过使用以下方法之一来请求 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 对象：  
  
-   派生自 <xref:Microsoft.VisualStudio.Shell.Package> 类的托管 VSPackage 的 <xref:System.IServiceProvider.GetService%2A> 方法。  有关更多信息，请参见[如何: 获取服务](~/extensibility/how-to-get-a-service.md)。  
  
-   静态 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 方法。  有关更多信息，请参见[如何：使用 GetGlobalService](~/misc/how-to-use-getglobalservice.md)。  
  
 在具有对 <xref:EnvDTE80.DTE2> 对象的访问权的 Visual Studio 扩展中，可以通过使用 <xref:Microsoft.VisualStudio.Shell.ServiceProvider> 对象的 <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> 方法来请求 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 对象。  有关更多信息，请参见[如何：从 DTE 对象获取服务](~/misc/how-to-get-a-service-from-the-dte-object.md)。  
  
### 示例  
 下面的代码示例演示如何在 Visual Studio 外接程序中检索项目服务。  若要使用此代码，请从外接程序项目的 `Connect` 类中运行此代码。  外接程序项目中会自动生成 `_applicationObject` 对象；此对象是 <xref:EnvDTE80.DTE2> 接口的一个实例。  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/cs/connect.cs#1)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/vb/connect.vb#1)]  
  
 此示例需要：  
  
-   Visual Studio 外接程序项目。  有关更多信息，请参见[如何：创建外接程序](http://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)。  
  
-   对 Microsoft.VisualStudio.OLE.Interop、Microsoft.VisualStudio.Shell 和 Microsoft.VisualStudio.SharePoint 程序集的引用。  
  
## 请参阅  
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [如何：创建外接程序](http://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)   
 [如何: 获取服务](~/extensibility/how-to-get-a-service.md)   
 [如何：从 DTE 对象获取服务](~/misc/how-to-get-a-service-from-the-dte-object.md)   
 [如何：使用向导来处理项目模板](~/extensibility/how-to-use-wizards-with-project-templates.md)  
  
  