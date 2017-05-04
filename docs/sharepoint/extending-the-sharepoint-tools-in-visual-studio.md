---
title: "Extending the SharePoint Tools in Visual Studio | Microsoft Docs"
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
  - "Visual Studio, extending tools"
  - "extensibility [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, extending tools"
ms.assetid: 084cf4bf-aaba-4277-8032-448f2cb2a124
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Extending the SharePoint Tools in Visual Studio
  在 Visual Studio 中的 SharePoint 工具与许多应用程序开发方案的要求。  但您可能会发现，有些情况下这些工具并不能提供您或其他开发人员需要的功能。  此时，您可以扩展 SharePoint 工具，创建所需功能。  
  
## 如何扩展 SharePoint 工具  
 可扩展 SharePoint 项目系统和**“服务器资源管理器”**窗口中的**“SharePoint 连接”**节点。  
  
### 扩展 SharePoint 项目系统  
 Visual Studio 提供了一组可用于创建 SharePoint 解决方案的项目模板和项模板。  例如事件接收器、列表定义、工作流和 Web 部件的模板。  但还可以定义您自己的 SharePoint 项目项类型，以创建 SharePoint 组件（如字段或自定义操作）。  也可以为 Visual Studio 中已安装的 SharePoint 项目项类型创建扩展，并可以为 SharePoint 项目创建扩展。  
  
 有关更多信息，请参见[Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)。  
  
### 扩展服务器资源管理器中的“SharePoint 连接”节点  
 在 Visual Studio 中，**服务器资源管理器** 可以使用 windows**SharePoint 连接** 节点查看一个或多个本地 SharePoint 网站组件的分层树视图中。 您可以通过以下方式扩展 **SharePoint 连接** 节点:  
  
-   添加自己的节点。  当希望显示默认情况下不显示的 SharePoint 网站的组件时，可以使用此方法。  
  
-   扩展现有节点。  例如，可以将一个新子节点添加到现有节点中，也可以将一个快捷菜单项添加到一个节点中，在开发人员单击该菜单项时执行相关任务。  
  
 有关更多信息，请参见[Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。  
  
## 开发计算机的要求  
 若要创建 SharePoint 工具扩展，开发计算机必须与创建 SharePoint 解决方案相同的要求在 Visual Studio。  有关更多信息，请参见[开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
 此外还建议您安装 [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。  SDK 包含可用于扩展 Visual Studio 的项目模板和工具。  具体而言，SDK 包含可用于轻松创建 Visual Studio 扩展 \(VSIX\) 包的项目模板。  VSIX 包是首选方法部署在 Visual Studio 的 Visual Studio 扩展。  所有 SharePoint 工具扩展都必须使用 VSIX 包来部署。  本文档中的所有演练都假定您已安装 [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。  
  
 若要下载 SDK，请访问 [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=164562](http://go.microsoft.com/fwlink/?LinkId=164562)。  有关 Visual Studio 扩展的更多信息，请参见[开发 Visual Studio 扩展](../Topic/Developing%20Visual%20Studio%20Extensions.md)。  
  
## 请参阅  
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Programming Concepts and Features for SharePoint Tools Extensions](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Reference &#40;SharePoint Tools Extensibility&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)   
 [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  