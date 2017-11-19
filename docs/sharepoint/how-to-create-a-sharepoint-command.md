---
title: "如何： 创建 SharePoint 命令 |Microsoft 文档"
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
helpviewer_keywords: SharePoint commands [SharePoint development in Visual Studio], creating
ms.assetid: e1fda8f0-eae1-4278-91c1-19a5e1fc327f
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 913ccb36c54914387cd6ca8a50a350ada1b14ce7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-a-sharepoint-command"></a>如何：创建 SharePoint 命令
  如果你想要在 SharePoint 工具扩展中使用服务器对象模型，则必须创建自定义*SharePoint 命令*调用 API。 在直接调用到服务器对象模型的程序集中定义 SharePoint 命令。  
  
 有关 SharePoint 命令的用途的详细信息，请参阅[调入 SharePoint 对象模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
### <a name="to-create-a-sharepoint-command"></a>若要创建 SharePoint 命令  
  
1.  创建一个类库项目具有以下配置：  
  
    -   以.NET Framework 3.5 为目标。 有关选择的目标框架的详细信息，请参阅[如何： 面向.NET Framework 版本](../ide/how-to-target-a-version-of-the-dotnet-framework.md)。  
  
    -   面向 AnyCPU 或 x64 平台。 默认情况下，类库项目的目标平台是 AnyCPU。 有关选择目标平台的详细信息，请参阅[如何： 向目标平台的配置项目](../ide/how-to-configure-projects-to-target-platforms.md)。  
  
    > [!NOTE]  
    >  不能定义 SharePoint 工具扩展中，同一项目中实现 SharePoint 命令，因为 SharePoint 命令面向.NET Framework 3.5 和 SharePoint 工具扩展目标[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]。 你必须定义你的扩展在单独的项目使用任何 SharePoint 命令。 有关详细信息，请参阅[部署 Visual Studio 中的 SharePoint 工具扩展](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
2.  添加对下列程序集的引用：  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
    -   Microsoft.SharePoint  
  
3.  在项目中的类，创建定义 SharePoint 命令的方法。 该方法必须遵循以下指导原则：  
  
    -   它可以具有一个或两个参数。  
  
         第一个参数必须是<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>对象。 此对象提供 Microsoft.SharePoint.SPSite 或 Microsoft.SharePoint.SPWeb 在其中执行此命令。 它还提供了<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger>可以用于将消息写入到对象**输出**窗口或**错误列表**Visual Studio 中的窗口。  
  
         第二个参数可以是一种类型的您的选择，但此参数是可选的。 如果你需要将数据从你的 SharePoint 工具扩展传递到命令，你可以向 SharePoint 命令添加此参数。  
  
    -   它可以具有返回值，但这是可选的。  
  
    -   第二个参数和返回值必须是可序列化的 Windows Communication Foundation (WCF) 的类型。 有关详细信息，请参阅[类型受数据协定序列化程序](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer)和[使用 XmlSerializer 类](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class)。  
  
    -   该方法可以具有任何可见性 (**公共**，**内部**，或**私有**)，而且它可以是静态或非静态。  
  
4.  应用<xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute>到方法。 此属性指定命令; 的唯一标识符此标识符没有以匹配的方法名称。  
  
     从 SharePoint 工具扩展调用命令时，你必须指定相同的唯一标识符。 有关详细信息，请参阅[如何： 执行 SharePoint 命令](../sharepoint/how-to-execute-a-sharepoint-command.md)。  
  
## <a name="example"></a>示例  
 下面的代码示例演示具有标识符 SharePoint 命令`Contoso.Commands.UpgradeSolution`。 此命令使用服务器对象模型中的 Api，升级到已部署的解决方案。  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]  
  
 除了隐式的第一个<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>参数，此命令还具有包含正在升级到 SharePoint 站点的.wsp 文件的完整路径的自定义字符串参数。 若要查看更大的示例的上下文中的此代码，请参阅[演练： 为 SharePoint 项目创建自定义部署步骤](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)。  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要引用以下程序集：  
  
-   Microsoft.VisualStudio.SharePoint.Commands  
  
-   Microsoft.SharePoint  
  
## <a name="deploying-the-command"></a>部署命令  
 若要部署命令，请将命令程序集包含在同一个[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]扩展 (VSIX) 包与扩展程序集，使用命令。 你还必须 extension.vsixmanifest 文件中的命令程序集添加一个条目。 有关详细信息，请参阅[部署 Visual Studio 中的 SharePoint 工具扩展](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另请参阅  
 [调入 SharePoint 对象模型](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [如何： 执行 SharePoint 命令](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [演练：扩展服务器资源管理器以显示 Web 部件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  