---
title: "如何： 执行 SharePoint 命令 |Microsoft 文档"
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
helpviewer_keywords: SharePoint commands [SharePoint development in Visual Studio], executing
ms.assetid: 2d1a163b-b601-4dac-bcea-328f24cb4d57
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f1cfe20d0cac50603265644fb48102ef22537631
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-execute-a-sharepoint-command"></a>如何：执行 SharePoint 命令
  如果你想要在 SharePoint 工具扩展中使用服务器对象模型，则必须创建自定义*SharePoint 命令*调用 API。 在定义该命令并将其部署与您的 SharePoint 工具扩展后，你的扩展可以执行命令来调入 SharePoint 服务器对象模型。 若要执行此命令，使用的一种 ExecuteCommand 方法<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>对象。  
  
 有关 SharePoint 命令的用途的详细信息，请参阅[调入 SharePoint 对象模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
### <a name="to-execute-a-sharepoint-command"></a>若要执行 SharePoint 命令  
  
1.  在 SharePoint 工具扩展中，获取<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>对象。 你获取的方法<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>对象取决于你创建的扩展的类型：  
  
    -   在 SharePoint 项目系统的扩展，使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A>属性。  
  
         有关项目系统扩展的详细信息，请参阅[扩展 SharePoint 项目系统](../sharepoint/extending-the-sharepoint-project-system.md)。  
  
    -   中的扩展**SharePoint 连接**中的节点**服务器资源管理器**，使用<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A>属性。 若要获取<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext>对象，请使用<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A>属性。  
  
         有关详细信息**服务器资源管理器**扩展，请参阅[扩展服务器资源管理器中的 SharePoint 连接节点](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。  
  
    -   在不是 SharePoint 工具，如项目模板向导中，扩展的一部分的代码使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A>属性。  
  
         有关检索该项目服务的详细信息，请参阅[使用 SharePoint 项目服务](../sharepoint/using-the-sharepoint-project-service.md)。  
  
2.  调用 ExecuteCommand 方法之一<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>对象。 传递的命令，你要执行到 ExecuteCommand 方法的第一个参数的名称。 如果你的命令有一个自定义参数，则将该参数传递给 ExecuteCommand 方法的第二个自变量。  
  
     没有为每个支持的命令签名不同 ExecuteCommand 重载。 下表列出了支持的签名和其重载，要用于每个签名。  
  
    |命令签名|要使用的 ExecuteCommand 重载|  
    |-----------------------|------------------------------------|  
    |该命令仅具有默认<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>参数，没有返回值。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |该命令仅具有默认<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>参数和返回值。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |该命令具有两个参数 (默认值<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>参数和自定义参数)，没有返回值。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |该命令还具有两个参数和返回值。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
  
## <a name="example"></a>示例  
 下面的代码示例演示如何使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>重载来调用`Contoso.Commands.UpgradeSolution`中所述的命令[如何： 创建 SharePoint 命令](../sharepoint/how-to-create-a-sharepoint-command.md)。  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]  
  
 `Execute`此示例中所示的方法是实现的<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A>方法<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>自定义部署步骤中的接口。 若要查看更大的示例的上下文中的此代码，请参阅[演练： 为 SharePoint 项目创建自定义部署步骤](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)。  
  
 请注意以下有关对的调用的详细信息<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>方法：  
  
-   第一个参数标识你想要调用的命令。 此字符串与匹配的值传递给<xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute>上的命令定义。  
  
-   第二个参数是你想要将传递给该命令的自定义第二个参数的值。 在这种情况下，它是正在升级到 SharePoint 站点的.wsp 文件的完整路径。  
  
-   该代码不会通过隐式<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>命令参数。 此参数被传递到命令自动从 SharePoint 项目系统的扩展或的扩展中调用该命令时**SharePoint 连接**中的节点**服务器资源管理器**. 在其他类型的解决方案，例如，实现的项目模板向导<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>接口，此参数是**null**。  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要 Microsoft.VisualStudio.SharePoint 程序集的引用。  
  
## <a name="see-also"></a>另请参阅  
 [调入 SharePoint 对象模型](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [如何： 创建 SharePoint 命令](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [演练：扩展服务器资源管理器以显示 Web 部件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  