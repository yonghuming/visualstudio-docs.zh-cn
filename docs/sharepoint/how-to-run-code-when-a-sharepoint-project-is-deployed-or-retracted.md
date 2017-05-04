---
title: "How to: Run Code When a SharePoint Project is Deployed or Retracted | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 353bbe6d-9b76-48ad-9fba-7e3c3712452f
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# How to: Run Code When a SharePoint Project is Deployed or Retracted
  如果要在部署或收回 SharePoint 项目时执行其他任务，您可以处理 Visual Studio 引发的事件。  有关更多信息，请参见[Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。  
  
### 在部署或收回 SharePoint 项目时运行代码  
  
1.  创建项目项扩展、项目扩展或新项目项类型的定义。  有关更多信息，请参见下列主题：  
  
    -   [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  在扩展中，访问 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 对象。  有关更多信息，请参见[How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)。  
  
3.  处理项目服务的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> 和 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> 事件。  
  
4.  在事件处理程序中，使用 <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> 参数来获取有关当前部署会话的信息。  例如，您可以确定哪个项目处于当前部署会话中，以及是否正在部署或收回该项目。  
  
 下面的代码示例演示如何在项目扩展中处理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> 和 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> 事件。  当 SharePoint 项目的部署启动和完成时，此扩展会向**“输出”**窗口中写入一条附加消息。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/handleprojectdeploymentevents.cs#12)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/handleprojectdeploymentevents.vb#12)]  
  
## 编译代码  
 此示例需要对以下程序集的引用：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 部署扩展  
 若要部署扩展，请为要随此扩展分发的程序集和任何其他文件创建 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 扩展 \(VSIX\) 包。  有关更多信息，请参见[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 请参阅  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)  
  
  