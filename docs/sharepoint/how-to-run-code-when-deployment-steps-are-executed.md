---
title: "How to: Run Code When Deployment Steps are Executed | Microsoft Docs"
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
ms.assetid: 6b0a52e5-e0ba-41bc-9e8a-1013e51fd3ba
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# How to: Run Code When Deployment Steps are Executed
  如果您希望为 SharePoint 项目中的部署步骤执行其他任务，则可以在 Visual Studio 执行每个部署步骤的前后处理由 SharePoint 项目项引发的事件。  有关更多信息，请参见[Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。  
  
### 在执行部署步骤时运行代码  
  
1.  创建项目项扩展、项目扩展或新项目项类型的定义。  有关更多信息，请参见下列主题：  
  
    -   [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  在扩展中，处理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> 对象（在项目项扩展或项目扩展中）或 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> 对象（在新项目项类型的定义中）的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> 和 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> 事件。  
  
3.  在事件处理程序中，使用 <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> 和 <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> 参数获取有关部署步骤的信息。  例如，您可以确定正在执行哪一个部署步骤以及是部署还是收回解决方案。  
  
## 示例  
 下面的代码示例演示如何在“列表实例”项目项的扩展中处理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> 和 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> 事件。  若 Visual Studio 在部署和收回解决方案时回收应用程序池，则此扩展会向**“输出”**窗口中写入一条附加消息。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/handledeploymentstepevents.cs#4)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/handledeploymentstepevents.vb#4)]  
  
## 编译代码  
 此示例需要对以下程序集的引用：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 部署扩展  
 若要部署扩展，请为要随此扩展分发的程序集和任何其他文件创建 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 扩展 \(VSIX\) 包。  有关更多信息，请参见[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 请参阅  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [How to: Run Code When a SharePoint Project is Deployed or Retracted](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)  
  
  