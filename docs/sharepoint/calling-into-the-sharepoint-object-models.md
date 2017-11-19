---
title: "调入 SharePoint 对象模型 |Microsoft 文档"
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
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint development in Visual Studio, server object model
- SharePoint commands [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extensibility features
ms.assetid: 99934f9e-901e-464e-ac8c-22c6c86440f4
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3bd3f81580af908d06fe7389c04a6559d14f1075
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="calling-into-the-sharepoint-object-models"></a>调入 SharePoint 对象模型
  当你在 Visual Studio 中创建 SharePoint 工具扩展时，你可能必须调用 SharePoint Api 来执行某些任务。 例如，如果创建 SharePoint 项目自定义部署步骤时，你可能需要调用 SharePoint Api 来执行一些任务来部署解决方案。  
  
 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]和[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]提供可以在 SharePoint 工具扩展中使用的两个不同的对象模型： 服务器对象模型和客户端对象模型。 每个对象模型在 SharePoint 工具扩展的上下文中具有的优点和缺点。  
  
 SharePoint 对象模型的概述，请参阅[的编程模型的 SharePoint 工具扩展的概述](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)。  
  
## <a name="using-the-client-object-model-in-extension-projects"></a>在扩展项目中使用的客户端对象模型  
 当开发 SharePoint 工具扩展时，你可以像任何其他组托管 Api 项目中使用的客户端对象模型。 你可以将客户端对象模型中的引用程序集添加到你的项目，并可以在代码中直接在客户端对象模型中调用 Api。  
  
 但是，客户端对象模型在 SharePoint 工具扩展的上下文中具有两个缺点：  
  
-   客户端对象模型提供的服务器对象模型的一个子集。 如果你需要使用不在客户端对象模型中公开的 SharePoint 功能，你必须使用服务器对象模型。  
  
-   虽然在大多数情况下，应运行在 SharePoint 工具扩展中使用的客户端对象模型，你可能会遇到某些情况下，其中对客户端对象模型的调用无法按预期工作。 客户端对象模型旨在用于在客户端应用程序中调入 SharePoint 站点上的远程服务器或场。 Visual Studio 中的 SharePoint 工具仅适用于开发计算机上的本地 SharePoint 安装。 因此，当你在 SharePoint 工具扩展中使用的客户端对象模型，调入 SharePoint 站点的本地计算机上，这是不如何的客户端对象模型旨在使用。  
  
 有关演示如何在 Visual Studio 中的 SharePoint 工具扩展中使用的客户端对象模型的演练，请参阅[演练： 调入 SharePoint 客户端对象模型在服务器资源管理器扩展](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)。  
  
## <a name="using-the-server-object-model-in-extension-projects"></a>在扩展项目中使用服务器对象模型  
 服务器对象模型是客户端对象模型的超集。 当你使用服务器对象模型时，你可以使用所有功能，[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]和[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]以编程方式公开。  
  
 SharePoint 工具扩展可以在服务器对象模型中，使用 Api，但它们不能直接调用的 Api。 面向.NET Framework 3.5 可以仅从 64 位进程调用服务器对象模型。 但是，SharePoint 工具扩展需要[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]和它们在 32 位 Visual Studio 进程中运行。 这可以防止 SharePoint 工具扩展直接引用 SharePoint 服务器对象模型中的程序集。  
  
 如果你想要在 SharePoint 工具扩展中使用服务器对象模型，则必须创建自定义*SharePoint 命令*调用 API。 在直接调用到服务器对象模型的辅助程序集中定义 SharePoint 命令。 在扩展项目中，则 SharePoint 命令间接使用调用 ExecuteCommand 付款方式<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>对象。  
  
 有关创建和使用 SharePoint 命令的详细信息，请参阅[如何： 创建 SharePoint 命令](../sharepoint/how-to-create-a-sharepoint-command.md)和[如何： 执行 SharePoint 命令](../sharepoint/how-to-execute-a-sharepoint-command.md)。 有关如何部署 SharePoint 命令的信息，请参阅[部署 Visual Studio 中的 SharePoint 工具扩展](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
 有关演示如何创建和使用 SharePoint 命令的演练，请参阅[演练： 为 SharePoint 项目创建自定义部署步骤](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)和[演练： 扩展服务器资源管理器显示 Web部分](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。  
  
### <a name="understanding-how-sharepoint-commands-are-executed"></a>了解如何 SharePoint 命令执行  
 定义 SharePoint 命令的程序集是在名为 vssphost4.exe 的 64 位主机进程中加载。 在 SharePoint 工具扩展中调用 SharePoint 命令后，通过 vssphost4.exe 而不是 32 位 Visual Studio 进程 (devenv.exe) 执行该命令。 你可以控制如何通过在注册表中设置值执行 SharePoint 命令的某些的方面。 有关详细信息，请参阅[调试 Visual Studio 中的 SharePoint 工具扩展](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 创建 SharePoint 命令](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [如何： 执行 SharePoint 命令](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [SharePoint 工具扩展的编程模型概述](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  