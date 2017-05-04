---
title: "How to: Create a SharePoint Command | Microsoft Docs"
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
  - "SharePoint commands [SharePoint development in Visual Studio], creating"
ms.assetid: e1fda8f0-eae1-4278-91c1-19a5e1fc327f
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# How to: Create a SharePoint Command
  若要在 SharePoint 工具扩展中使用服务器对象模型，必须创建自定义 SharePoint 命令以调用 API。  在可直接调入服务器对象模型的程序集中定义 SharePoint 命令。  
  
 有关 SharePoint 命令的用途的更多信息，请参见[Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
### 创建 SharePoint 命令  
  
1.  创建一个具有以下配置的类库项目：  
  
    -   以 .NET Framework 3.5 为目标。  有关选择目标框架的更多信息，请参见[如何：面向 .NET Framework 的某个版本](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md)。  
  
    -   以 AnyCPU 或 x64 平台为目标。  默认情况下，类库项目的目标平台是 AnyCPU。  有关选择目标平台的更多信息，请参见[NIB: How to: Optimize an Application for a Specific CPU Type](http://msdn.microsoft.com/zh-cn/294a75d2-4279-4b72-8298-2bea05be907a)。  
  
    > [!NOTE]  
    >  无法在定义 SharePoint 工具扩展的相同项目中实现 SharePoint 命令，因为 SharePoint 命令面向 .NET Framework 3.5，而 SharePoint 工具扩展面向 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]。  必须在单独的项目中定义由您的扩展使用的任何 SharePoint 命令。  有关更多信息，请参见[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
2.  添加对下列程序集的引用：  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
    -   Microsoft.SharePoint  
  
3.  在项目的类中，创建一个定义 SharePoint 命令的方法。  该方法必须符合下列准则：  
  
    -   该方法可以具有一个或两个参数。  
  
         第一个参数必须是 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 对象。  此对象提供要在其中执行所定义的命令的 Microsoft.SharePoint.SPSite 或 Microsoft.SharePoint.SPWeb。  此对象还提供可用于将消息写入到 Visual Studio 中的**“输出”**窗口或**“错误列表”**窗口的 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> 对象。  
  
         第二个参数可以是您选择的类型，但此参数是可选的。  如果您需要将 SharePoint 工具扩展中的数据传递给 SharePoint 命令，则可以将此参数添加到该命令中。  
  
    -   该方法还可以具有一个返回值，但此值是可选的。  
  
    -   第二个参数和返回值必须属于可由 Windows Communication Foundation \(WCF\) 序列化的类型。  有关更多信息，请参见[数据协定序列化程序支持的类型](../Topic/Types%20Supported%20by%20the%20Data%20Contract%20Serializer.md)和[使用 XmlSerializer 类](../Topic/Using%20the%20XmlSerializer%20Class.md)。  
  
    -   该方法可以具有任何可见性（**public**、**internal** 或 **private**），并且它可以是静态的也可以是非静态的。  
  
4.  将 <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> 应用于该方法。  此特性指定命令的唯一标识符；此标识符不必与方法名匹配。  
  
     当从 SharePoint 工具扩展调用该命令时，必须指定相同的唯一标识符。  有关更多信息，请参见[How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md)。  
  
## 示例  
 下面的代码示例演示一个标识符为 `Contoso.Commands.UpgradeSolution` 的 SharePoint 命令。  此命令使用服务器对象模型中的 API 来升级到部署的解决方案。  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/sharepointcommands/commands.vb#5)]  
  
 除第一个隐式 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 参数外，此命令还具有一个自定义字符串参数，该参数包含要升级到 SharePoint 网站的 .wsp 文件的完整路径。  若要在一个更大的示例上下文中查看此代码，请参见[Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)。  
  
## 编译代码  
 此示例需要对以下程序集的引用：  
  
-   Microsoft.VisualStudio.SharePoint.Commands  
  
-   Microsoft.SharePoint  
  
## 部署命令  
 若要部署命令，请将相应的命令程序集与使用该命令的扩展程序集一起包括在同一 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 扩展 \(VSIX\) 包中。  还必须在 extension.vsixmanifest 文件中为该命令程序集添加一个条目。  有关更多信息，请参见[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 请参阅  
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  