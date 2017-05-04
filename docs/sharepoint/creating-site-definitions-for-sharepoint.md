---
title: "创建 SharePoint 网站定义 | Microsoft Docs"
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
  - "Visual Studio 中的 SharePoint 开发，网站定义"
  - "网站定义 [Visual Studio 中的 SharePoint 开发]"
ms.assetid: 83db570d-6b9f-4dab-9e71-db41f17b987a
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# 创建 SharePoint 网站定义
  通过 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的 SharePoint 网站定义项目，您可以创建将用作新 SharePoint 网站的基础的网站定义。  这些定义不仅确定 SharePoint 网站的外观和行为，还确定网站的默认内容和功能。  在定义您可以放入预配置的列表、内容类型、事件接收器、图像以及其他项。  例如 SharePoint 包含某些网站定义，例如 BLOG。  根据 BLOG 网站定义创建网站时，网站中将包含列表、Web 部件以及博客网站所需的其他项。  
  
 有关网站定义的更多信息，请参见 [网站模板和定义](http://go.microsoft.com/fwlink/?LinkId=179134)。  
  
## 网站定义项目  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的网站定义项目只提供 SharePoint 网站所需的基本文件，而不提供任何默认功能。  您必须添加文件和内容来提供所需的功能。  可以通过创建并添加所需的文件来手动构建网站。  
  
## 功能附加  
 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中创建网站定义的一个优点是，这些定义会自动使用功能附加。  功能附加是将一个功能附加到网站定义中，而不是在网站定义自身中嵌入其功能。  通过此操作，您可以将功能添加到使用网站定义创建的任何网站中，而无需修改原始网站定义。  有关更多信息，请参见 [功能附加功能](http://go.microsoft.com/fwlink/?LinkID=119283)。  
  
## 网站定义项目组件  
 创建网站定义解决方案时，将向其**“SiteDefinition”**节点中添加以下默认文件。  
  
|文件名|说明|  
|---------|--------|  
|default.aspx|新 SharePoint 网站的默认 ASPX 主页。|  
|onet.xml|指定新网站的配置、网站定义模板的组件以及默认行为。  这些设置可以包括启用的内容类型、默认列表视图、文档模板文件和网站附带的 Web 部件等特性。  默认情况下，`Modules` 部分会列出将添加到 SharePoint 网站中的文件及其配置方式。|  
|webtemp\_*SiteDefinitionName*.xml|指定**“新建 SharePoint 站点”**页的**“模板选择”**部分中显示的网站定义配置。|  
  
 默认情况下，所有网站定义都存储在*drive:*\\Program Files\\Common Files\\Microsoft Shared\\Web Server Extensions\\14\\TEMPLATE\\SiteTemplates 文件夹中。  每个网站定义都有自己的子文件夹。  
  
## 相关主题  
  
|标题|说明|  
|--------|--------|  
|[演练：创建基本网站定义项目](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|分步指导您在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中创建基本网站定义项目。|  
|[如何：创建自定义站点定义和配置。](http://go.microsoft.com/fwlink/?LinkId=183309)|描述如何通过复制现有网站定义并修改复制内容，在 SharePoint 中创建自定义网站定义。|  
|[WebTemp.xml](http://go.microsoft.com/fwlink/?LinkId=183310)|描述指定**“新建 SharePoint 站点”**页的**“模板选择”**部分可用的网站定义的原始文件。|  
|[本地化 SharePoint 解决方案](../sharepoint/localizing-sharepoint-solutions.md)|介绍如何准备 SharePoint 解决方案以供全局使用。|  
|[为 SharePoint 创建 Web 部件](../sharepoint/creating-web-parts-for-sharepoint.md)|说明如何创建用户可以修改的 SharePoint 页面的各个部分。|  
|[为 Web 部件或应用程序页创建可重用控件](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|说明如何创建可在应用程序页和 Web 部件中运行的可重用控件。|  
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|说明如何使用在项目中打开网页时出现的设计器。|  
|[ASP.NET 网页概述](http://go.microsoft.com/fwlink/?LinkId=178726)|提供有关 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 网页结构、[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 如何处理页面，以及 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 页如何显示按 XHTML 标准编译的标记的常规信息。|  
|[ASP.NET 网页语法概述](http://go.microsoft.com/fwlink/?LinkId=178727)|说明构成 ASP.NET 页面的标记元素。|  
|[ASP.NET 网页编程](http://go.microsoft.com/fwlink/?LinkId=178728)|提供有关如何在 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 页中创建事件处理程序以及如何使用客户端脚本的信息。|  
|[Windows SharePoint Services 编程](http://go.microsoft.com/fwlink/?LinkId=178729)|说明如何使用 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 中提供的托管对象模型。|  
  
## 请参阅  
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  