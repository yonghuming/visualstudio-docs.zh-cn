---
title: "How to: Execute a SharePoint Command | Microsoft Docs"
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
  - "SharePoint commands [SharePoint development in Visual Studio], executing"
ms.assetid: 2d1a163b-b601-4dac-bcea-328f24cb4d57
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# How to: Execute a SharePoint Command
  若要在 SharePoint 工具扩展中使用服务器对象模型，必须创建自定义 SharePoint 命令以调用 API。  在定义该命令并将其与 SharePoint 工具扩展一起部署之后，您的扩展可以执行该命令以调入 SharePoint 服务器对象模型。  若要执行该命令，请使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> 对象的 ExecuteCommand 方法之一。  
  
 有关 SharePoint 命令的用途的更多信息，请参见[Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
### 执行 SharePoint 命令  
  
1.  在 SharePoint 工具扩展中，获取 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> 对象。  获取 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> 对象的方式取决于所创建的扩展的类型：  
  
    -   在 SharePoint 项目系统的扩展中，使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> 属性。  
  
         有关项目系统扩展的更多信息，请参见[Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)。  
  
    -   在**“服务器资源管理器”**中的**“SharePoint 连接”**节点的扩展中，使用 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> 属性。  若要获取 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> 对象，请使用 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> 属性。  
  
         有关**“服务器资源管理器”**扩展的更多信息，请参见[Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。  
  
    -   在不属于 SharePoint 工具（如项目模板向导）扩展的一部分的代码中，使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> 属性。  
  
         有关检索项目服务的更多信息，请参见[Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)。  
  
2.  调用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> 对象的 ExecuteCommand 方法之一。  将要执行的命令的名称传递给 ExecuteCommand 方法的第一个参数。  如果您的命令具有一个自定义参数，请将该参数传递给 ExecuteCommand 方法的第二个参数。  
  
     针对每个支持的命令签名的 ExecuteCommand 重载各不相同。  下表列出了支持的签名以及用于每个签名的重载。  
  
    |命令签名|要使用的 ExecuteCommand 重载|  
    |----------|----------------------------|  
    |此命令仅具有默认的 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 参数，没有返回值。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |此命令仅具有默认的 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 参数和一个返回值。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |此命令具有两个参数（默认的 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 参数和一个自定义参数），没有返回值。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |此命令具有两个参数和一个返回值。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
  
## 示例  
 下面的代码示例演示如何使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> 重载来调用[How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)中所述的 `Contoso.Commands.UpgradeSolution` 命令。  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/deploymentstepextension/upgradestep.vb#6)]  
  
 此示例中演示的 `Execute` 方法是自定义部署步骤中的 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> 接口的 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> 方法的实现。  若要在一个更大的示例上下文中查看此代码，请参见[Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)。  
  
 请注意下面有关 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> 方法调用的详细信息：  
  
-   第一个参数标识要调用的命令。  此字符串与传递给命令定义上的 <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> 的值匹配。  
  
-   第二个参数是要传递给命令的第二个自定义参数的值。  在本例中，该参数是要升级到 SharePoint 网站的 .wsp 文件的完整路径。  
  
-   此代码不会将隐式 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 参数传递给命令。  当从 SharePoint 项目系统的扩展或**“服务器资源管理器”**中的**“SharePoint 连接”**节点的扩展中调用该命令时，此参数会自动传递给该命令。  在其他类型的解决方案中（如在实现 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 接口的项目模板向导中），此参数为 **null**。  
  
## 编译代码  
 此示例需要引用 Microsoft.VisualStudio.SharePoint 程序集。  
  
## 请参阅  
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  