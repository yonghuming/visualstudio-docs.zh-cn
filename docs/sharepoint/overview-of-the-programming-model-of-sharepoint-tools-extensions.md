---
title: "Overview of the Programming Model of SharePoint Tools Extensions | Microsoft Docs"
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
  - "Visual Studio, extending tools"
  - "SharePoint development in Visual Studio, extensibility object models"
  - "SharePoint development in Visual Studio, extending tools"
ms.assetid: aec8165b-dff9-47be-82a5-3fa38e579297
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# Overview of the Programming Model of SharePoint Tools Extensions
  在 Visual Studio 中创建 SharePoint 工具扩展时，首先将实现由 SharePoint 工具公开的一个或多个扩展性接口。  在大多数情况下，你还将使用 SharePoint 工具提供的其他类型来实现扩展中的功能。  在某些方案中，你还可以使用 Visual Studio 和 SharePoint 提供的其他对象模型中的类型。  你必须了解每个对象模型的用途以及如何将这些对象模型结合使用，以创建 SharePoint 工具扩展。  
  
## 通过实现扩展性接口来扩展 SharePoint 工具  
 Visual Studio 使用 .NET Framework 4 中的 Managed Extensibility Framework \(MEF\) 为 SharePoint 工具提供扩展性模型。  MEF 是一个在 System.ComponentModel.Composition 程序集中实现的 API，它使应用程序能够公开扩展性点，并在运行时发现和加载扩展。  有关 MEF 的详细信息，请参阅 [Managed Extensibility Framework &#40;MEF&#41;](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)。  
  
 若要扩展 SharePoint 工具，请实现由 Visual Studio 公开的一个或多个扩展性接口。  必要时，你还必须将 <xref:System.ComponentModel.Composition.ExportAttribute> 和其他特定于 SharePoint 工具的特性应用于接口实现。  下表列出了一些接口，可实现这些接口以扩展 SharePoint 工具。  
  
|接口|描述|  
|--------|--------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|实现此接口可定义新类型的 SharePoint 项目项。  有关示例，请参阅[How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|实现此接口可扩展已在 Visual Studio 中安装的 SharePoint 项目项类型。  有关示例，请参阅[How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|实现此接口可扩展 SharePoint 项目。  有关示例，请参阅[How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。|  
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|实现此接口可定义一个可在部署或撤消 SharePoint 项目项时执行的新部署步骤。  有关示例，请参阅[Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)。|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|实现此接口可在**“服务器资源管理器”**窗口中的**“SharePoint 连接”**节点下展开现有节点。  有关示例，请参阅[How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|实现此接口可在**“服务器资源管理器”**窗口中的**“SharePoint 连接”**节点下定义新类型的节点。  有关示例，请参阅[How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|实现此接口可定义自定义功能验证规则。  有关示例，请参阅[How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)。|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|实现此接口可定义自定义包验证规则。  有关示例，请参阅[How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)。|  
  
 在实现 SharePoint 工具扩展后，必须在 Visual Studio 扩展 \(VSIX\) 包中部署扩展程序集，才能允许 Visual Studio 发现和加载该扩展。  有关详细信息，请参阅[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 了解在 SharePoint 工具扩展中使用的对象模型  
 在创建 SharePoint 工具扩展时可使用多种对象模型：  
  
-   *SharePoint 工具对象模型*。  此对象模型提供了扩展性接口（可实现这些接口以创建 SharePoint 工具扩展）和其他相关类型。  
  
-   *Visual Studio 自动化对象模型和集成对象模型*。  使用这些对象模型可访问 SharePoint 工具对象模型范围之外的 Visual Studio 功能。  
  
    > [!NOTE]  
    >  利用 SharePoint 项目服务，可以将 SharePoint 工具对象模型中的一些对象转换为 Visual Studio 自动化对象模型和集成对象模型中的对象，或进行相反的转换。  有关详细信息，请参阅[Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)。  
  
-   *SharePoint 服务器对象模型和客户端对象模型*。  使用这些对象模型可从 SharePoint 工具扩展的上下文中修改 SharePoint 站点或检索 SharePoint 站点中的数据。  
  
### SharePoint 工具对象模型  
 每个 SharePoint 工具扩展都使用 SharePoint 工具对象模型中的类型来定义扩展的核心行为和功能。  下表描述此对象模型中包含的命名空间。  
  
|程序集|命名空间|描述|  
|---------|----------|--------|  
|Microsoft.VisualStudio.SharePoint.dll|<xref:Microsoft.VisualStudio.SharePoint>|包含用于扩展和自动化 SharePoint 项目系统的类型。  例如，你可以扩展内置 SharePoint 项目和项目项，也可以创建自己的项目项。  有关详细信息，请参阅[Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)。|  
||<xref:Microsoft.VisualStudio.SharePoint.Deployment>|包含用于扩展 SharePoint 项目的部署过程（例如，创建你自己的部署步骤和部署配置）的类型。  有关详细信息，请参阅[Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。|  
||<xref:Microsoft.VisualStudio.SharePoint.Explorer>|包含用于在**“服务器资源管理器”**窗口中的**“SharePoint 连接”**节点下展开节点或定义新类型的节点的类型。  有关详细信息，请参阅[Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。|  
||<xref:Microsoft.VisualStudio.SharePoint.Features>|包含用于访问 SharePoint 项目中的功能定义的类型。|  
||<xref:Microsoft.VisualStudio.SharePoint.Packages>|包含用于访问 SharePoint 解决方案中的包定义的类型。|  
||<xref:Microsoft.VisualStudio.SharePoint.Validation>|包含用于为 SharePoint 项目自定义功能和包验证行为的类型。  有关详细信息，请参阅[How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)。|  
|Microsoft.VisualStudio.SharePoint.Commands.dll|<xref:Microsoft.VisualStudio.SharePoint.Commands>|包含用于创建自定义 *SharePoint 命令*的类型。  SharePoint 命令是一个用于从 SharePoint 工具扩展中调入 SharePoint 服务器对象模型的方法。  有关详细信息，请参阅[Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)。|  
|Microsoft.VisualStudio.SharePoint.Explorer.Extensions.dll|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|包含可用于获取有关内置**“服务器资源管理器”**节点的信息的类型，这些节点表示 SharePoint 站点上的各个组件，如表示列表、字段或内容类型的节点。  有关详细信息，请参阅[Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。|  
  
### Visual Studio 自动化对象模型  
 Visual Studio 自动化对象模型提供可用于自动化 Visual Studio 项目和 IDE 的 API。  使用 Visual Studio 对象模型可执行与项目相关的任务（非 SharePoint 项目专用任务），或执行 Visual Studio 中的其他常规自动化任务。  虽然从传统上说，此对象模型通常在 Visual Studio 外接程序和宏中使用，但你也可以在 SharePoint 工具扩展中使用它。  
  
 EnvDTE.dll 程序集中定义了 Visual Studio 自动化对象模型的主要部分。  EnvDTE80.dll、EnvDTE90.dll、EnvDTE100.dll 和 EnvDTE110.dll 程序集分别提供在 Visual Studio 2005、Visual Studio 2008、Visual Studio 2010 和 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] 中引入的其他功能。  这些程序集包含在 Visual Studio 中。  
  
 有关自动化对象模型的详细信息，请参阅[扩展 Visual Studio 环境](http://msdn.microsoft.com/library/4173a963-7ac7-4966-9bb7-e28a9d9f6792)和[自动化与扩展性参考](http://msdn.microsoft.com/library/93112562-db21-4188-9383-ed19ad79bddf)。  
  
### Visual Studio 集成对象模型  
 集成对象模型提供了一些 API，可以使用这些 API 通过创建 *VSPackage* 来向 Visual Studio 中添加功能。  VSPackage 是一个模块，它通过提供自定义功能（如工具窗口、编辑器、设计器、服务和项目）来扩展 Visual Studio IDE。  
  
 若要添加将用于内置 SharePoint 工具的新 Visual Studio 功能，则可以使用集成对象模型。  例如，如果创建一个表示 SharePoint 站点的自定义操作的自定义 SharePoint 项目项，则也可以创建一个实现该自定义操作的设计器的 VSPackage。  你可以将设计器与自定义操作关联，方法是向**“解决方案资源管理器”**中表示该自定义操作的项目项添加快捷菜单项。  可以通过打开其快捷菜单（通过右键单击自定义操作项目项，或通过选择自定义操作项目然后选择 SHIFT \+ F10 键），然后选择**“打开”**来打开设计器。  
  
 Visual Studio SDK 附带的一组程序集中定义了此对象模型。  此对象模型中的一些主程序集中包含 Microsoft.VisualStudio.Shell.11.0.dll、Microsoft.VisualStudio.Shell.Interop.dll 和 Microsoft.VisualStudio.OLE.Interop.dll。  
  
 有关集成对象模型的详细信息，请参阅 [Visual Studio 扩展性体系结构](/visual-cpp/misc/visual-studio-extensibility-architecture)和 [Visual Studio SDK 参考](../extensibility/visual-studio-sdk-reference.md)。  
  
### SharePoint 对象模型  
 SharePoint 工具扩展可以使用 SharePoint API 来修改 SharePoint 站点或从 SharePoint 站点检索数据。  [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 和 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 提供了两个不同的对象模型：服务器对象模型和客户端对象模型。  
  
 可以在 SharePoint 工具扩展中使用任一对象模型中的 API，但在 SharePoint 工具扩展的上下文中，每个对象模型均有各自的优点和缺点。  有关详细信息，请参阅[Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
|对象模型|描述|  
|----------|--------|  
|服务器对象模型|通过服务器对象模型，可以访问 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 和 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 以编程方式公开的所有功能。  此对象模型旨在供在 SharePoint Server 上运行的 SharePoint 解决方案使用。  Microsoft.SharePoint.dll 程序集中定义了此对象模型的大部分内容。  有关服务器对象模型的详细信息，请参阅[使用 SharePoint Foundation 服务器端对象模型](http://go.microsoft.com/fwlink/?LinkId=177796)。|  
|客户端对象模型|客户端对象模型是服务器对象模型的子集，可用于从远程客户端或服务器与 SharePoint 数据进行互操作。  它旨在将执行常见任务时必须执行的往返次数减至最小。  Microsoft.SharePoint.Client.dll 和 Microsoft.SharePoint.Client.Runtime.dll 程序集中定义了客户端对象模型的大部分内容。  有关客户端对象模型的详细信息，请参阅[托管客户端对象模型](http://go.microsoft.com/fwlink/?LinkId=177797)。|  
  
## 请参阅  
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)  
  
  