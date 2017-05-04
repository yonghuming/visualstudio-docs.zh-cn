---
title: "沙盒解决方案与场解决方案之间的差异 | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "场解决方案 [Visual Studio 中的 SharePoint 开发]"
  - "沙盒解决方案 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 场解决方案"
  - "Visual Studio 中的 SharePoint 开发, 沙盒解决方案"
ms.assetid: 43beb7e7-0cd9-4a8f-bb72-6b1e0cba5be8
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# 沙盒解决方案与场解决方案之间的差异
  在编译 SharePoint 解决方案时，该解决方案将部署到 SharePoint 服务器，并将附加调试器以对其进行调试。  用于调试解决方案的过程取决于沙盒解决方案属性的设置：沙盒解决方案或场解决方案。  
  
 有关更多信息，请参见[沙盒解决方案注意事项](../sharepoint/sandboxed-solution-considerations.md)。  
  
## 场解决方案  
 场解决方案承载于 IIS 辅助进程 \(W3WP.exe\) 中，将运行会影响整个场的代码。  在调试其“沙盒解决方案”属性设置为“场解决方案”的 SharePoint 项目时，系统的 IIS 应用程序池会在 SharePoint 收回或部署功能之前进行回收，以便发布由 IIS 辅助进程锁定的任何文件。  仅回收为 SharePoint 项目的网站 URL 服务的 IIS 应用程序池。  
  
## 沙盒解决方案  
 沙盒解决方案承载于 SharePoint 用户代码解决方案辅助进程 \(SPUCWorkerProcess.exe\) 中，将运行只会影响解决方案的网站集的代码。  由于沙盒解决方案不在 IIS 辅助进程中运行，因此 IIS 应用程序池和 IIS 服务器都无需重新启动。  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将调试器附加到 SPUCWorkerProcess 进程，SharePoint 中的 SPUserCodeV4 服务将自动触发和控制该进程。  SPUCWorkerProcess 进程无需回收即可加载最新版本的解决方案。  
  
## 任一类型的解决方案  
 无论使用哪一类解决方案，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 都会将调试器附加到浏览器以启用客户端脚本调试。  为实现此目的，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将使用脚本调试引擎。  若要启用脚本调试，您必须在收到系统提示时更改默认浏览器设置。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 只会将调试器附加到运行当前网站的 W3WP 或 SPUCWorkerProcess 进程。  此外，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 还附加托管 COM Plus 和工作流调试引擎。  
  
## 请参阅  
 [调试 SharePoint 解决方案](../sharepoint/debugging-sharepoint-solutions.md)   
 [生成和调试 SharePoint 解决方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [沙盒解决方案注意事项](../sharepoint/sandboxed-solution-considerations.md)  
  
  