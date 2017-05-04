---
title: "Extending the SharePoint Project System | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: 654b2973-a5c9-44be-a3d2-8bc3d15f9624
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Extending the SharePoint Project System
  可以创建 SharePoint 解决方案使用安装项目模板和项模板在 Visual Studio。  这些模板符合许多开发方案的要求，但是，您会发现它们不提供所需的功能的情形。  在这些情况下，您可以扩展 SharePoint 项目系统。  
  
## SharePoint 项目系统概述  
 SharePoint 项目系统基于 SharePoint 项目项的基本组件。  SharePoint 项目项表示单个 SharePoint 自定义设置，如列表定义、Web 部件或内容类型。  
  
 SharePoint 项目是一个 Visual Studio 项目，它包括一个或多个 SharePoint 项目项。  SharePoint 项目还包含其他组件，这些组件定义如何将项目项编组到功能和包中以进行部署。  
  
 有关 SharePoint 项目项和 SharePoint 项目的内容的更多信息，请参见[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
## 如何扩展 SharePoint 项目系统  
 您可以通过以下方式扩展 SharePoint 项目系统：  
  
-   定义您自己的 SharePoint 项目项类型，并将它们与 Visual Studio 中新的项模板或项目模板相关联。  例如，可以定义一个 SharePoint 项目项类型以创建自定义操作或字段。  有关更多信息，请参见[Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)。  
  
-   扩展 Visual Studio 中已安装的 SharePoint 项目项类型。  例如，那么，当开发人员选择菜单项时，可以添加快捷菜单项添加到 **解决方案资源管理器** 的项目项和自定义项目项。  有关更多信息，请参见[Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)。  
  
-   扩展 SharePoint 项目。  例如，可以添加事件处理程序，以便当在 SharePoint 项目中添加或移除项时执行特定任务。  有关更多信息，请参见[Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)。  
  
-   扩展 SharePoint 项目项和 SharePoint 项目的打包和部署行为。  例如，可以创建在部署或收回项目时要执行的自己的部署步骤，也可以在 Visual Studio 执行特定部署步骤时，执行附加的自定义任务。  有关更多信息，请参见[Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。  
  
## 常规开发任务  
 可以在 SharePoint 项目系统扩展中执行以下常规任务：  
  
-   将自定义字符串数据与项目项一起保存到多种不同类型的项目文件中。  有关更多信息，请参见[Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。  
  
-   将 SharePoint 项目系统中的对象转换为 Visual Studio 自动化对象模型或集成对象模型中的相应对象，或进行反向转换。  有关更多信息，请参见[Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)。  
  
## 请参阅  
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Programming Concepts and Features for SharePoint Tools Extensions](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
  
  