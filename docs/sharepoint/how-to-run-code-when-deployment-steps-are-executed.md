---
title: "如何： 执行代码部署步骤时运行 |Microsoft 文档"
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
ms.assetid: 6b0a52e5-e0ba-41bc-9e8a-1013e51fd3ba
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e1aed7e4fe7ee30450b3ec37ce36616648e830fa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>如何：在执行部署步骤时运行代码
  如果你想要执行部署步骤 SharePoint 项目中的其他任务，你可以处理由 SharePoint 项目项之前和 Visual Studio 执行每个部署步骤后引发的事件。 有关详细信息，请参阅[扩展 SharePoint 打包和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。  
  
### <a name="to-run-code-when-deployment-steps-are-executed"></a>若要执行部署步骤时运行代码  
  
1.  创建项目项扩展、 项目扩展或新的项目项类型的定义。 有关详细信息，请参阅下列主题：  
  
    -   [如何：创建 SharePoint 项目项扩展](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [如何：创建 SharePoint 项目扩展](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [如何：定义 SharePoint 项目项类型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  在扩展中，处理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>和<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted>的事件<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>（在项目项扩展或项目扩展） 的对象或<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>（中的一个新的项目项类型定义） 的对象。  
  
3.  在事件处理程序，使用<xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs>和<xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs>参数来获取部署步骤的信息。 例如，您可以确定执行哪个部署步骤，以及是否正在解决方案部署或收回。  
  
## <a name="example"></a>示例  
 下面的代码示例演示如何处理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>和<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted>列表实例项目项扩展中的事件。 此扩展将其他消息写入**输出**窗口在 Visual Studio 部署和收回解决方案，而回收应用程序池时。  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要引用以下程序集：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>部署扩展  
 若要部署的扩展，创建[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]扩展 (VSIX) 包的程序集和你想要随此扩展分发的任何其他文件。 有关详细信息，请参阅[部署 Visual Studio 中的 SharePoint 工具扩展](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另请参阅  
 [扩展 SharePoint 打包和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [演练： 为 SharePoint 项目创建自定义部署步骤](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [如何：在部署或收回 SharePoint 项目时运行代码](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)  
  
  