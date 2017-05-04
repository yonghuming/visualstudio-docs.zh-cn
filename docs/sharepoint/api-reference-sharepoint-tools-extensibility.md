---
title: "API Reference (SharePoint Tools Extensibility) | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, reference for project and tools extensibility"
ms.assetid: 3a42dacd-0213-4c25-aeba-9b6935ab70db
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# API Reference (SharePoint Tools Extensibility)
  本节包含有关在 Visual Studio 中扩展 SharePoint 工具的 API 参考文档。  
  
## 本节内容  
 <xref:Microsoft.VisualStudio.SharePoint>  
 包含用于扩展 SharePoint 项目系统的类型。  例如，您可以扩展内置 SharePoint 项目和项目项，也可以创建自己的项目项。  
  
 <xref:Microsoft.VisualStudio.SharePoint.Commands>  
 包含用于创建自定义 SharePoint 命令的类型。  SharePoint 命令是一个用于从 SharePoint 工具扩展中调入 SharePoint 服务器对象模型的方法。  
  
 <xref:Microsoft.VisualStudio.SharePoint.Deployment>  
 包含用于扩展 SharePoint 项目的部署过程的类型。  
  
 <xref:Microsoft.VisualStudio.SharePoint.Explorer>  
 包含用于扩展**“服务器资源管理器”**中的 SharePoint 节点或定义自己的节点类型的类型。  
  
 <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>  
 包含可用于获取有关内置**“服务器资源管理器”**节点的信息的类型，这些节点表示 SharePoint 网站上的各个组件，如表示列表、字段或内容类型的节点。  
  
 <xref:Microsoft.VisualStudio.SharePoint.Features>  
 包含用于访问 SharePoint 项目中的功能定义的类型。  
  
 <xref:Microsoft.VisualStudio.SharePoint.Packages>  
 包含用于访问 SharePoint 项目中的包定义的类型。  
  
 <xref:Microsoft.VisualStudio.SharePoint.Remote.Authentication>  
 包含用于SharePoint 身份验证和与部署在远程 SharePoint 站点应用程序进行沟通的类型。  
  
 <xref:Microsoft.VisualStudio.SharePoint.Remote.Commands>  
 包含用于创建用于部署在远程 SharePoint 站点上的SharePoint应用程序的远程SharePoint命令的类型 。  
  
 <xref:Microsoft.VisualStudio.SharePoint.Tasks>  
 包含 Visual Studio 使用作为生成打包和调试 SharePoint 项目任务，Office应用程序 和 SharePoint应用程序的类型。  此 API 支持 Office 和 SharePoint 基础结构，不应在代码中直接使用。  
  
 <xref:Microsoft.VisualStudio.SharePoint.Validation>  
 包含用于为 SharePoint 项目自定义功能和包验证行为的类型。  
  
## 请参阅  
 [Reference &#40;SharePoint Tools Extensibility&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)   
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)  
  
  