---
title: "为 SharePoint 创建页 | Microsoft Docs"
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
  - "内容页 [Visual Studio 中的 SharePoint 开发], 设计"
  - "母版页 [Visual Studio 中的 SharePoint 开发], 设计"
  - "页面布局 [Visual Studio 中的 SharePoint 开发], 设计"
  - "Visual Studio 中的 SharePoint 开发, 内容页"
  - "Visual Studio 中的 SharePoint 开发, 母版页"
  - "Visual Studio 中的 SharePoint 开发, 页面布局"
ms.assetid: 57678ed1-841f-45de-a1d3-5f9e233bf3ce
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 为 SharePoint 创建页
  可以为 SharePoint 站点创建应用程序页、网站页、母版页和页面布局。  
  
 可以使用 Visual Studio 中的模板创建应用程序页。  使用 SharePoint Designer 创建网站页、母版页和页面布局。  然后，可以将这些页导入到 Visual Studio 以在 SharePoint 项目中使用。  
  
 还可以使用级联样式表、ECMAScript 和主题来修改页的外观和行为。  
  
## SharePoint 页的类型  
 下表描述了 SharePoint 网站包含的页的四种主要类型。  
  
|页类型|说明|  
|---------|--------|  
|应用程序页|如果您希望页包含自定义代码，或者需要在多个网站中共享页，请创建应用程序页。  否则，最好是选择创建网站页。|  
|网站页|若要执行下列任何任务，请创建网站页：<br /><br /> -   向 SharePoint 库添加页。<br />-   使页能够承载动态 Web 部件和 Web 部件区域等功能。<br />-   使用户能够使用 SharePoint Designer 自定义页。<br /><br /> 如果您希望页面包含自定义代码，请不要创建网站页。  尽管您可以将自定义代码添加到网站页中，但如果用户使用 SharePoint Designer 自定义该页，代码将停止运行。|  
|母版页|如果您要定义网站页和应用程序页的通用结构，请创建母版页。|  
|页面布局|页面布局是 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 特有的，使您能够进一步定义网站页和应用程序页的通用结构。|  
  
 有关每种类型的页的概述，请参见 [生成块：页面和用户界面](http://go.microsoft.com/fwlink/?LinkID=182095)，和 [页面布局和母版页](http://go.microsoft.com/fwlink/?LinkID=182096)。  
  
## 创建应用程序页  
 通过向 SharePoint 项目添加**“应用程序页”**项，可以在 Visual Studio 中创建应用程序页。  可以将控件添加到该页，然后通过添加代码来处理控件事件。  
  
 可以在该页的代码文件中设置断点，启动调试器，然后在本地 SharePoint 网站上测试该页，而无需执行任何其他配置步骤。  有关详细信息，请参阅[为 SharePoint 创建应用程序页](../sharepoint/creating-application-pages-for-sharepoint.md)。  
  
## 创建网站页、母版页和页面布局  
 可以使用 SharePoint Designer 创建网站页、母版页和页面布局。  然后，可以将这些页导入到 Visual Studio 中。  若要利用 Visual Studio 中提供的部署或源代码管理功能，请导入这些页。  有关详细信息，请参阅[从现有的 SharePoint 网站导入项](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)。  
  
 由于这些页在导入后很难进行修改，因此您应先设计好这些页，然后再导入它们。  
  
## 创建级联样式表、ECMAScript 和主题  
 Visual Studio 不提供用于开发 SharePoint 网站的级联样式表 \(CSS\)、ECMAScript \(JavaScript, JScript\) 或主题文件的模板。  可以使用 SharePoint SDK 中提供的指南或使用 SharePoint Designer 这样的工具来创建这些文件。  
  
 可以直接将这些文件添加到解决方案中，也可以导入这些文件。  在任一情况下，您必须为添加的每个项创建相应的映射文件夹。  有关如何创建映射文件夹的更多信息，请参见[如何：添加和移除映射文件夹](../sharepoint/how-to-add-and-remove-mapped-folders.md)。  
  
 有关如何创建级联样式表的更多信息，请参见 [级联样式表类在 SharePoint Foundation 中的用法](http://go.microsoft.com/fwlink/?LinkID=182098)。  有关如何为 SharePoint 解决方案创建 JavaScript 和 JScript 文件的更多信息，请参见 [设置 ECMAScript 的基本 ASPX 页](http://go.microsoft.com/fwlink/?LinkID=182099)。  有关主题的更多信息，请参见 [生成块：页面和用户界面](http://go.microsoft.com/fwlink/?LinkID=182095)。  
  
## 相关主题  
  
|标题|说明|  
|--------|--------|  
|[为 SharePoint 创建应用程序页](../sharepoint/creating-application-pages-for-sharepoint.md)|介绍如何添加应用程序页（即，与 SharePoint 母版页合并的 .aspx 内容）。|  
|[如何：创建应用程序页](../sharepoint/how-to-create-an-application-page.md)|演示如何创建在 SharePoint 网站上运行的 ASP.NET 页。|  
|[演练：创建 SharePoint 应用程序页](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|演示如何设计和调试 SharePoint 站点的 ASP.NET 网页。|  
|[使用 Visual Web Developer](http://msdn.microsoft.com/zh-cn/9c31f93b-c8fb-4599-9b14-6194ec8c7539)|说明如何使用在项目中打开网页时出现的设计器。|  
  
  