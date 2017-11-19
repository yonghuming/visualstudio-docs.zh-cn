---
title: "如何： 运行代码 SharePoint 项目时是部署或收回 |Microsoft 文档"
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
helpviewer_keywords: SharePoint development in Visual Studio, extending deployment
ms.assetid: 353bbe6d-9b76-48ad-9fba-7e3c3712452f
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0650bfdb7961728fed34147c05f6333d8255e373
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>如何：在部署或收回 SharePoint 项目时运行代码
  如果你想要部署或收回 SharePoint 项目时执行其他任务，你可以处理由 Visual Studio 引发的事件。 有关详细信息，请参阅[扩展 SharePoint 打包和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。  
  
### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>若要运行代码时 SharePoint 项目部署或收回  
  
1.  创建项目项扩展、 项目扩展或新的项目项类型的定义。 有关详细信息，请参阅下列主题：  
  
    -   [如何：创建 SharePoint 项目项扩展](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [如何：创建 SharePoint 项目扩展](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [如何：定义 SharePoint 项目项类型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  在扩展中，访问<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>对象。 有关详细信息，请参阅[如何： 检索 SharePoint 项目服务](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)。  
  
3.  处理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted>和<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted>项目服务的事件。  
  
4.  在事件处理程序，使用<xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs>参数，以获取有关当前部署会话的信息。 例如，您可以确定哪些项目是在当前部署会话中以及是否正在部署或收回。  
  
 下面的代码示例演示如何处理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted>和<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted>项目扩展中的事件。 此扩展将其他消息写入**输出**窗口部署开始和完成为 SharePoint 项目时。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要引用以下程序集：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>部署扩展  
 若要部署的扩展，创建[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]扩展 (VSIX) 包的程序集和你想要随此扩展分发的任何其他文件。 有关详细信息，请参阅[部署 Visual Studio 中的 SharePoint 工具扩展](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另请参阅  
 [扩展 SharePoint 打包和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [如何：在执行部署步骤时运行代码](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)  
  
  