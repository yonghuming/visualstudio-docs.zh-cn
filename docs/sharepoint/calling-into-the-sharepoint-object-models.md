---
title: "Calling into the SharePoint Object Models | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, client object model"
  - "SharePoint development in Visual Studio, server object model"
  - "SharePoint commands [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, extensibility features"
ms.assetid: 99934f9e-901e-464e-ac8c-22c6c86440f4
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Calling into the SharePoint Object Models
  在 Visual Studio 中创建 SharePoint 工具扩展，您可能必须调用 SharePoint API 来执行某些任务。  例如，因此，如果 SharePoint 项目创建自定义部署步骤，您可能必须调用 SharePoint API 来执行某些任务部署解决方案。  
  
 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 和 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 提供可在 SharePoint 工具扩展中使用的两个不同的对象模型:服务器对象模型和客户端对象模型。  每个对象模型均有各自的优点和缺点。 SharePoint 工具扩展的上下文中。  
  
 有关 SharePoint 对象模型的概述，请参见 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)。  
  
## 在扩展项目中使用客户端对象模型  
 在开发 SharePoint 工具扩展时，则与任何其他的项目中使用客户端对象模型设置托管 API。  您可以添加对客户端对象模型的程序集添加到项目，因此，您可以调用客户端对象模型中的 API 直接从代码。  
  
 但是，客户端对象模型具有两个缺点在 SharePoint 工具扩展中:  
  
-   客户端对象模型仅提供服务器对象模型的子集。  如果您必须使用客户端对象模型中未显示的 SharePoint 功能，则必须使用服务器对象模型。  
  
-   虽然使用客户端对象模型在 SharePoint 工具扩展应在许多情况下工作，可能会遇到对客户端的情况对象模型不按预期进行的。  客户端对象模型旨在供客户端应用程序调入 SharePoint 远程服务器或场的站点。  在 Visual Studio 中的 SharePoint 工具仅适用于开发计算机上的本地 SharePoint 安装一起使用。  因此，那么，当您在 SharePoint 工具扩展中使用客户端对象模型，您在本地计算机上调入 SharePoint 网站，而是如何设计为使用客户端对象模型。  
  
 有关演示如何使用客户端在 SharePoint 扩展的对象模型在 Visual Studio 工具的演练，请参见 [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)。  
  
## 在扩展项目中使用服务器对象模型  
 服务器对象模型是客户端对象模型的超集。  在使用服务器对象模型时，可以使用 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 和 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 编程方式公开的所有功能。  
  
 SharePoint 工具扩展可以使用服务器对象模型中的 API，，但不能直接调用这些 API。  服务器对象模型可以从 64 位仅调用处理面向 .NET framework 3.5。  但是， SharePoint 工具扩展需要 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ，并在 32 位 Visual Studio 进程中运行。  这将阻止 SharePoint 工具扩展直接引用 SharePoint 服务器对象模型中的程序集。  
  
 若要在 SharePoint 工具扩展中使用服务器对象模型，必须创建自定义 *SharePoint* 命令调用 API。  您将在可直接调入服务器对象模型的辅助程序集的 SharePoint 命令。  使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> 对象的 ExecuteCommand 方法，在扩展项目中，则间接调用 SharePoint 命令。  
  
 有关创建和使用 SharePoint 命令的更多信息，请 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md) 参见和 [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md)。  有关如何部署 SharePoint 命令的信息，请参见 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
 有关演示如何创建，并使用 SharePoint 命令的演练，请参见和 [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。  
  
### 了解如何执行 SharePoint 命令  
 定义 SharePoint 命令的程序集在 64 位宿主进程中加载名为 vssphost4.exe。  在调用在 SharePoint 工具扩展后的 SharePoint 命令，该命令将由 vssphost4.exe 执行而不是 32 位 Visual Studio 进程 \(devenv.exe\)。  您可以控制某些方面的 SharePoint 命令如何通过设置注册表中的值执行。  有关更多信息，请参见 [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 请参阅  
 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  