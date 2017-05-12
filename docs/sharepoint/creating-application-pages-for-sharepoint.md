---
title: "为 SharePoint 创建应用程序页"
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
  - "应用程序页 [Visual Studio 中的 SharePoint 开发], 创建"
  - "应用程序页 [Visual Studio 中的 SharePoint 开发], 开发"
  - "Visual Studio 中的 SharePoint 开发, 应用程序页"
  - "Visual Studio 中的 SharePoint 开发, 内容页"
  - "Visual Studio 中的 SharePoint 开发, 网页"
ms.assetid: a6e97149-15dd-4bdb-8d75-3b53f886f76c
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# 为 SharePoint 创建应用程序页
  应用程序页是设计用于 SharePoint 网站的 ASP.NET 网页。  应用程序页是 ASP.NET 页的专用类型。  应用程序页和标准 ASP.NET 页之间的主要区别在于，应用程序页包含的内容与 SharePoint 母版页合并。  母版页使应用程序页能够与站点上的其他页共享相同的外观和行为。  
  
 通过 Visual Studio，您可以使用设计器设计应用程序页。  设计器可显示在母版页中定义的每个内容占位符的内容区域。  可以通过将控件拖动到这些内容区域设计应用程序页。  
  
## 应用程序页  
 应用程序页在服务器上的所有网站之间共享，而网站页则特定于一个网站。  有关更多信息，[SharePoint 页的类型](http://go.microsoft.com/fwlink/?LinkID=211584)。  
  
 默认情况下，创建 SharePoint 网站时显示的大多数页都是网站页面。  可以将网站页面添加到 SharePoint 页库中。  用户可以使用 SharePoint Designer 等工具来自定义网站页面。  网站页面还可以承载动态 Web 部件和 Web 部件区域等功能。  
  
 应用程序页不能执行这些操作。  但是，如果您希望页包含自定义代码，则应用程序页是要创建的最佳类型页。  尽管您可以将自定义代码添加到网站页面中，但如果用户使用 SharePoint Designer 等工具自定义该页，代码将停止运行。  
  
> [!NOTE]  
>  Visual Studio 不提供可帮助您创建 SharePoint 站点的网站页面的模板。  有关更多信息，请参见[SharePoint 页的类型](http://go.microsoft.com/fwlink/?LinkID=211584)。  
  
## 创建应用程序页  
 若要创建应用程序页，请向 SharePoint 项目添加**“应用程序页”**项。  当您创建应用程序页时，Visual Studio 将向项目中添加下列文件夹：  
  
|文件夹|说明|  
|---------|--------|  
|Layouts|映射到 SharePoint 文件系统的 \_layouts 虚拟目录。|  
|Layouts 子文件夹|包含构成应用程序页的文件。  默认情况下，此文件夹的名称与项目名称相同。  您随时都可以重命名此文件夹。  当您运行项目时，Visual Studio 会将此文件夹部署到 SharePoint 文件系统的 \_layouts 虚拟目录。|  
  
 Visual Studio 向项目添加下列文件：  
  
|文件|说明|  
|--------|--------|  
|ASP.NET 页文件 \(.aspx\)|包含用于定义页的 XML 标记。|  
|应用程序页代码文件|包含应用程序页背后的代码。  请向此文件添加用于处理事件的代码。|  
|应用程序页设计器代码文件|包含由设计器生成的代码。  不要直接编辑此文件。|  
  
## 设计和调试应用程序页  
 可以使用 Visual Studio 中的 Visual Web Developer 设计器设计应用程序页的内容。  在您打开项目中的应用程序页\(双击或通过打开其快捷菜单中选择 **打开**\)，此设计器会出现。  有关如何使用此设计器的更多信息，请参见 [Visual Studio Web 开发环境内容映射](http://msdn.microsoft.com/zh-cn/9c31f93b-c8fb-4599-9b14-6194ec8c7539)。  
  
> [!NOTE]  
>  您只能在设计器的**“源”**视图中设计页。  为应用程序页禁用了设计器的**“设计”**视图。  
  
 您可以调试应用程序页，就像在 Visual Studio 中调试其他 SharePoint 项目项一样。  当您启动 Visual Studio 调试器时，Visual Studio 将打开 SharePoint 站点。  
  
 若要查看应用程序页，您必须手动定位到应用程序页的位置（例如：http:\/\/*Server\_Name*\/\_layouts\/*Project\_Name*\/ApplicationPage1.aspx）。  
  
 有关如何调试 SharePoint 项目的更多信息，请参见[SharePoint 解决方案疑难解答](../sharepoint/troubleshooting-sharepoint-solutions.md)。  
  
## 选择母版页  
 默认情况下，**“应用程序页”**项引用您要用来调试项目的站点的母版页。  该页名为 v4.master，并且在 SharePoint 网站的**“母版页样式库”**中列出。  
  
 通过设置应用程序 `Page` 元素的 `MasterPageFile` 特性，可以显式更改应用程序页使用的母版页。（例如：`MasterPageFile="~/_layouts/applicationv4.master"`）。  实际上，如果没有在 SharePoint 服务器上启用动态母版页，则必须设置此特性。  有关 SharePoint 中母版页的更多信息，请参见 [母版页](http://go.microsoft.com/fwlink/?LinkID=169281)。  
  
## 请参阅  
 [SharePoint Foundation 的详细开发](http://go.microsoft.com/fwlink/?LinkID=182103)   
 [ASP.NET 网页概述](http://msdn.microsoft.com/library/52fa0455-41ea-4315-8208-2861d1527da2)   
 [ASP.NET 网页语法概述](http://msdn.microsoft.com/library/09074b20-ece9-46fa-bc8f-ab2595ed2c02)   
 [ASP.NET 网页编程](http://msdn.microsoft.com/zh-cn/5626c661-8057-4de8-b658-c2e35ed4b4c9)  
  
  