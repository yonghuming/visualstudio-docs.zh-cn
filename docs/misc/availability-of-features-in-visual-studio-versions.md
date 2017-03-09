---
title: "Visual Studio 各版本中的功能可用性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio, 功能的可用性"
ms.assetid: cb2728da-7705-4dea-a1c3-12a0388cb652
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Visual Studio 各版本中的功能可用性
下表显示 Visual Studio Professional 的所列版本是否支持某些功能。  
  
-   “是”表示 Visual Studio 版本中包括相应功能。  
  
-   “添加”表示 Visual Studio 版本中不包括相应功能，但该功能可用，并且通过单击链接可了解详细信息。  
  
-   “否”表示 Visual Studio 版本中不包括相应功能。  
  
||Visual Studio 2010<br /><br /> 和<br /><br /> Visual Studio 2010 SP1|[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]|[!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]|  
|-|---------------------------------------------------------|-------------------------------------------------------------------|--------------------------------------------------------------|  
|支持的 .NET Framework 版本|2.0、3.0、3.5 SP1、4|2.0、3.0、3.5 SP1、4、4.5|2.0、3.0、3.5 SP1、4、4.5、4.5.1|  
|本地 Web 服务器|是|是|是|  
|SQL Server Express|2008|2008|2008|  
|通过服务器资源管理器连接到 SQL Server 版本|2000, 2005, 2008|2000, 2005, 2008|2000, 2005, 2008|  
|ASP.NET AJAX <sup>1</sup>|是|是|是|  
|ASP.NET 模型视图控制器|是|是|是|  
|ASP.NET 动态数据|是|是|是|  
|MSBuild|是|是|是|  
|ADO.NET Entity Framework|是|是|是|  
|ADO.NET 数据服务|是|是|是|  
|Microsoft Azure Tools|添加|添加||  
|智能设备|否|否||  
|并行计算|是 <sup>2</sup>|是|是|  
|Windows Communication Foundation|是|是|是|  
|Windows Presentation Foundation|是|是|是|  
|.NET 丰富 Internet 应用程序服务|[添加](http://go.microsoft.com/fwlink/?LinkID=230768)|是|是|  
|Silverlight 1|是|是|是|  
|Silverlight 2|否|是|是|  
|Silverlight 3|是|是|是|  
|Silverlight 4|[添加](http://go.microsoft.com/fwlink/?LinkID=153710)|是|是|  
|Silverlight 5|[添加](http://go.microsoft.com/fwlink/?LinkID=215392)，仅限 SP1。|是|是|  
|IronPython|[添加](http://go.microsoft.com/fwlink/?LinkID=183863)|[添加](http://go.microsoft.com/fwlink/?LinkID=183863)|[添加](http://go.microsoft.com/fwlink/?LinkID=183863)|  
|IronRuby|[添加](http://go.microsoft.com/fwlink/?LinkID=183864)|[添加](http://go.microsoft.com/fwlink/?LinkID=183864)|[添加](http://go.microsoft.com/fwlink/?LinkID=183864)|  
|Visual Studio Tools for Office|是 <sup>4</sup><br /><br /> （Office 2007、Office 2010）|是 <sup>4</sup>\(Office 2010\)|是 <sup>4</sup>\(Office 2013\)|  
|报表项目|是|是|是|  
|报表向导|是|是|是|  
|语言集成查询 \(LINQ\)|是|是|是|  
|SharePoint 开发|是，面向 SharePoint 2010|是，面向 SharePoint 2010|是，面向 SharePoint 2013|  
|.NET Framework 4 Client Profile 支持|是|No|否|  
  
1.  ASP.NET AJAX：  
  
     服务器端：控件包括在 ASP.NET 3.5 中，并且 Visual Studio 的**“工具箱”**中已提供。  如果你使用的是 ASP.NET 的早期版本（例如，ASP.NET 2.0），则可下载 [ASP.NET AJAX 扩展](http://go.microsoft.com/fwlink/?LinkID=75360)。  
  
     客户端：客户端 ASP.NET AJAX Library 包含在 ASP.NET 3.5 SP1 中。  
  
2.  并行计算：  
  
     并行扩展包含任务并行库 \(TPL\)、并行 LINQ \(PLINQ\) 和并发数据结构；.NET Framework 4 中包含这些组件。  用于本机 C\+\+ 开发的等效库有并发运行时和代理库，在 Visual Studio 2010 中包含这些库。  Visual Studio 2010 中还包含探查器和调试器增强功能。  
  
3.  IronPython 和 IronRuby：  
  
     在针对 IronPython 和 IronRuby 的 CodePlex 网站中，提供了几个版本。  选择适用于你的环境的版本。  这两种语言的最低要求均为 .NET Framework 2.0 SP1。  
  
4.  Visual Studio Tools for Office \(VSTO\) 兼容性和外接程序功能：  
  
    ||Visual Studio 2010|[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]|[!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]|  
    |-|------------------------|-------------------------------------------------------------------|--------------------------------------------------------------|  
    |文档级|Word 2007、Word 2010、Excel 2007、Excel 2010|Word 2010、Excel 2010|Word 2013、Excel 2013|  
    |应用程序级|Word 2007、Word 2010、Excel 2007、Excel 2010、InfoPath 2007、InfoPath 2010、Outlook 2007、Outlook 2010、PowerPoint 2007、PowerPoint 2010、Visio 2007、Visio 2010、Project 2007、Project 2010|Word 2010、Excel 2010、InfoPath 2010、Outlook 2010、PowerPoint 2010、Visio 2010、Project 2010|Word 2013、Excel 2013、InfoPath 2013、Outlook 2013、PowerPoint 2013、Visio 2013、Project 2013|