---
title: "如何： 处理部署冲突 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SharePoint development in Visual Studio, extending deployment
ms.assetid: 8e545873-3fed-46cf-a95f-27b5fc0d5f83
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0ca793132fcf2f3e5e2a84d5289bcfb20f61d591
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-handle-deployment-conflicts"></a>如何：处理部署冲突
  你可以提供你自己的代码来处理部署冲突 SharePoint 项目项。 例如，您可以确定是否当前的项目项中的任何文件在部署位置中，已存在，然后删除已部署的文件，然后部署当前的项目项。 有关部署冲突的详细信息，请参阅[扩展 SharePoint 打包和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。  
  
### <a name="to-handle-a-deployment-conflict"></a>若要处理部署冲突  
  
1.  创建项目项扩展、 项目扩展或新的项目项类型的定义。 有关详细信息，请参阅下列主题：  
  
    -   [如何：创建 SharePoint 项目项扩展](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [如何：创建 SharePoint 项目扩展](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [如何：定义 SharePoint 项目项类型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  在扩展中，处理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>事件<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>（在项目项扩展或项目扩展） 的对象或<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>（中的一个新的项目项类型定义） 的对象。  
  
3.  事件处理程序中，确定是否存在正在部署的项目项与设置部署的解决方案在 SharePoint 站点上，根据适用于你的方案的条件发生冲突。 你可以使用<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A>要分析正在部署的项目项的事件自变量参数的属性并且可以通过调用 SharePoint 命令为此目的定义分析部署位置处的文件。  
  
     对于许多类型的冲突，你可能首先需要确定执行哪个部署步骤。 你可以执行此操作通过使用<xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A>事件自变量参数的属性。 尽管通常最好在内置过程中检测冲突<xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution>部署步骤，你可以检查冲突在任何部署步骤。  
  
4.  如果存在冲突，使用<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A>方法<xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A>的事件参数以创建一个新的属性<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>对象。 此对象表示部署冲突。 调用中<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A>方法，还指定调用来解决冲突的方法。  
  
## <a name="example"></a>示例  
 下面的代码示例演示了处理部署冲突的列表定义项目项的项目项扩展中的基本过程。 若要处理不同类型的项目项部署冲突，不同将字符串传递给<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>。 有关详细信息，请参阅[扩展 SharePoint 项目项](../sharepoint/extending-sharepoint-project-items.md)。  
  
 为简单起见，<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>事件处理程序在此示例假定存在部署冲突 (即，它始终将添加一个新<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>对象)，和`Resolve`方法只返回**true** ，则指示已解决冲突。 在实际方案中，你<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>事件处理程序将首先确定是否在当前的项目项中的文件和部署位置中，在文件之间存在冲突，然后添加<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>仅对象是否存在冲突。 例如，你可能使用`e.ProjectItem.Files`分析中的项目项，并且你的文件的事件处理程序中的属性可能调用 SharePoint 命令来分析部署位置处的文件。 同样，在实际情况中`Resolve`方法可能调用 SharePoint 命令来解决在 SharePoint 站点冲突。 有关创建 SharePoint 命令的详细信息，请参阅[如何： 创建 SharePoint 命令](../sharepoint/how-to-create-a-sharepoint-command.md)。  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs#1)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要引用以下程序集：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>部署扩展  
 若要部署的扩展，创建[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]扩展 (VSIX) 包的程序集和你想要随此扩展分发的任何其他文件。 有关详细信息，请参阅[部署 Visual Studio 中的 SharePoint 工具扩展](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另请参阅  
 [扩展 SharePoint 打包和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [扩展 SharePoint 项目项](../sharepoint/extending-sharepoint-project-items.md)   
 [如何： 在执行运行代码时部署步骤](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [如何：创建 SharePoint 命令](../sharepoint/how-to-create-a-sharepoint-command.md)  
  
  