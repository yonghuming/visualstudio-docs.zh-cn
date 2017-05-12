---
title: "沙盒解决方案注意事项"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.SandboxedSolutions"
  - "VS.SharePointTools.Security.SandboxedSolutions"
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
ms.assetid: 6c2d2dc6-4acb-4b68-ba94-a61087e8dff0
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# 沙盒解决方案注意事项
  沙盒解决方案是 Microsoft SharePoint 2010 中包含的一项功能，此功能使网站集用户能够上载自己的自定义代码解决方案。  常见的沙盒解决方案是用户上载自己的 Web 部件。  
  
 沙盒 SharePoint 应用程序在一个安全的、受监视的进程中运行，它只能访问 Web 场的有限部分。  Microsoft SharePoint 2010 利用功能组合、解决方案库、解决方案监控和验证框架来启用沙盒解决方案。  
  
## 指定项目信任级别  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 通过一个名为 *Sandboxed Solution* 的 Boolean 项目属性来支持沙盒解决方案。  既可以随时在项目中设置此属性，也可以在**“SharePoint 自定义向导”**中创建项目时指定此属性。  
  
> [!NOTE]  
>  在创建项目后更改项目的 *Sandboxed Solution* 属性可能会导致出现验证错误。  
  
 如果将 *Sandboxed Solution* 属性设置为 **false**，或选择**“部署为场解决方案”**选项，则解决方案将被视为作用域为场的解决方案。  不过，如果将 *Sandboxed Solution* 属性设置为 **true**，或选择向导中的**“部署为沙盒解决方案”**选项，则解决方案将不被视为场解决方案。  
  
## SharePoint 网站层次结构  
 若要理解沙盒解决方案的工作方式，了解 SharePoint 网站的作用域是分层的这一点会很有用。  顶部元素称作 Web 场，其他元素从属于顶部元素：  
  
 Web 场  
  
 Web 应用程序 A  
  
 网站集 A1  
  
 网站 A1a  
  
 Web 应用程序 B  
  
 网站集 B1  
  
 网站 B1a  
  
 网站 B1b  
  
 网站集 B2  
  
 网站 B2a  
  
 如您所见，Web 场可以包含一个或多个 Web 应用程序，Web 应用程序又可以包含一个或多个网站集，而网站集又可以包含子网站，依此类推。  对一个网站集所做的更改只会影响该网站集，而不会影响其他网站集。  不过，在 Web 场级别所做的更改会影响该场中的所有网站集。  
  
 Windows SharePoint Services \(WSS\) 3.0 只允许您将解决方案部署到场级别，而 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 允许您将解决方案部署到场级别（场解决方案）或网站集级别（沙盒解决方案）。  
  
## 为什么使用沙盒解决方案？  
 在 WSS 3.0 中，只能将解决方案部署到场级别。  这意味着，可能会部署潜在有害或不稳定的解决方案，从而影响整个 Web 场以及在场中运行的所有其他网站集和应用程序。  不过，通过使用沙盒解决方案，您可以将解决方案部署到场的子区域（一个特定的网站集）。  为了提供额外保护，不会将解决方案的程序集加载到主 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 进程 \(w3wp.exe\) 中，  而是将其加载到单独的进程 \(SPUCWorkerProcess.exe\) 中。  此进程将会受到监控，并实现配额和调节以防止场中出现执行有害活动（例如运行消耗 CPU 周期的紧凑循环）的沙盒解决方案。  
  
## 网站集解决方案库  
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 包含一项名为“网站集解决方案库的功能”。您可以访问此功能，从SharePoint 2010 管理中心"页或通过打开 **网站操作** 菜单，选择 **站点设置**，然后选择 **解决方案** 链接在 SharePoint 站点下的  **库** 。  解决方案库是解决方案的储存库，网站集管理员可以利用这些储存库来管理其网站集中的解决方案。  
  
 解决方案库是一个存储在 SharePoint 网站的根 Web 目录的文档库。  解决方案库代替了网站模板并支持解决方案包。  在上载 SharePoint 解决方案包 \(.wsp\) 文件时，会将该文件作为沙盒解决方案进行处理。  
  
## 沙盒解决方案限制  
 在部署沙盒解决方案时，可用于沙盒解决方案的 SharePoint 功能集是有限的，这有助于减少其可能具有的任何安全漏洞。  其中的一些限制包括：  
  
-   沙盒解决方案只能使用有限的一部分可部署解决方案元素。  可能容易受到攻击的 SharePoint 项目模板（如网站定义和工作流）将不可用。  
  
-   SharePoint 在一个独立于主 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 应用程序池 \(w3wp.exe\) 进程的进程 \(SPUCWorkerProcess.exe\) 中运行沙盒解决方案代码。  
  
-   不能将映射文件夹添加到项目中。  
  
-   不能在沙盒解决方案中使用 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 程序集 Microsoft.Office.Server 中的类型。  而只能在沙盒解决方案中使用 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 程序集 Microsoft.SharePoint 中的类型。  
  
 需要特别注意的是，将 SharePoint 解决方案指定为沙盒解决方案对 SharePoint Server 没有任何影响；这样做只会确定将 SharePoint 项目从 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 部署到 SharePoint 的方式以及该项目将绑定到的程序集。  这不会影响生成的 .wsp 文件，并且该 .wsp 文件不包含直接与 *Sandboxed Solution* 属性相关联的数据。  
  
## 沙盒解决方案中的功能和元素  
 沙盒解决方案支持以下功能和元素：  
  
-   内容类型\/字段  
  
-   自定义操作  
  
-   声明性工作流  
  
-   事件接收器  
  
-   功能标注  
  
-   列表定义  
  
-   列表实例  
  
-   模块\/文件  
  
-   导航  
  
-   Onet.xml  
  
-   SPItemEventReceiver  
  
-   SPListEventReceiver  
  
-   SPWebEventReceiver  
  
-   对派生自 `System.Web.UI.WebControls.WebParts.WebPart` 的所有 Web 部件的支持  
  
-   Web 部件  
  
-   WebTemplate 功能元素（而不是 Webtemp.xml）  
  
-   可视 Web 部件  
  
 沙盒解决方案不支持以下功能和元素：  
  
-   应用程序页  
  
-   自定义操作组  
  
-   场作用域内的功能  
  
-   `HideCustomAction` 元素  
  
-   Web 应用程序作用域内的功能  
  
-   包含代码的工作流  
  
## 请参阅  
 [沙盒解决方案与场解决方案之间的差异](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)   
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  