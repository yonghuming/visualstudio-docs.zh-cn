---
title: "How to: Handle Deployment Conflicts"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 8e545873-3fed-46cf-a95f-27b5fc0d5f83
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# How to: Handle Deployment Conflicts
  可以提供自己的代码以处理 SharePoint 项目项的部署冲突。  例如，您可以确定当前项目项中的任何文件是否已位于部署位置，然后在部署当前项目项之前删除已部署的文件。  有关部署冲突的更多信息，请参见[Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。  
  
### 处理部署冲突  
  
1.  创建项目项扩展、项目扩展或新项目项类型的定义。  有关更多信息，请参见下列主题：  
  
    -   [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  在扩展中，处理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> 对象（在项目项扩展或项目扩展中）或 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> 对象（在新项目项类型的定义中）的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> 事件。  
  
3.  在事件处理程序中，根据适用于您的方案的标准来确定 SharePoint 网站上正在部署的项目项与已部署的解决方案之间是否发生冲突。  可以使用事件实参参数的 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> 属性来分析正在部署的项目项，并且可以通过调用为此定义的 SharePoint 命令来分析位于部署位置的文件。  
  
     对于很多类型的冲突，您可能先要确定正在执行的部署步骤。  可以使用事件实参参数的 <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> 属性来做到这一点。  虽然在内置 <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> 部署步骤中检测冲突通常会有用，但可以在任何部署步骤中检查冲突。  
  
4.  如果存在冲突，则使用事件实参参数的 <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> 属性的 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> 方法来创建新的 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> 对象。  此对象表示部署冲突。  在调用 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> 方法时，还要指定解决冲突需调用的方法。  
  
## 示例  
 下面的代码示例演示处理列表定义项目项的项目项扩展中的部署冲突的基本过程。  若要处理不同类型的项目项的部署冲突，请将不同的字符串传递到 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>。  有关更多信息，请参见[Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)。  
  
 为简单起见，本示例中的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> 事件处理程序假定存在部署冲突（即，总是添加新的 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> 对象），而 `Resolve` 方法只返回 **true** 以指示已解决冲突。  在实际方案中，<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> 事件处理程序会先确定当前项目项中的文件和位于部署位置的文件之间是否存在冲突，然后仅在存在冲突时添加 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> 对象。  例如，可以使用事件处理程序中的 `e.ProjectItem.Files` 属性来分析项目项中的文件，并且可以调用 SharePoint 命令来分析位于部署位置的文件。  类似地，在实际方案中，`Resolve` 方法可以调用 SharePoint 命令来解决 SharePoint 网站上存在的冲突。  有关创建 SharePoint 命令的更多信息，请参见[How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.deploymentconflict/cs/extension/deploymentconflictextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.deploymentconflict/vb/extension/deploymentconflictextension.vb#1)]  
  
## 编译代码  
 此示例需要对以下程序集的引用：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 部署扩展  
 若要部署扩展，请为要随此扩展分发的程序集和任何其他文件创建 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 扩展 \(VSIX\) 包。  有关更多信息，请参见[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 请参阅  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)  
  
  