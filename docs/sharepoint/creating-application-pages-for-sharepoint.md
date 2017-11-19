---
title: "为 SharePoint 创建应用程序页 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web pages
- SharePoint development in Visual Studio, content pages
- SharePoint development in Visual Studio, application pages
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
ms.assetid: a6e97149-15dd-4bdb-8d75-3b53f886f76c
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 858df05759f1c3b4205d4cbcd0bbad2cdfb6e034
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-application-pages-for-sharepoint"></a>为 SharePoint 创建应用程序页
  *应用程序页*是一个 ASP.NET Web 页，可用于 SharePoint 的网站。 应用程序页是 ASP.NET 页的专用的类型。 应用程序页和一个标准的 ASP.NET 页的主要区别是应用程序页包含与 SharePoint 母版页合并的内容。 母版页使应用程序页可以为站点上的其他页面共享相同的外观和行为。  
  
 Visual Studio，可通过使用设计器来设计应用程序页。 设计器显示在母版页中定义的每个内容占位符内容区域。 你可以通过将控件拖到这些内容区域来设计应用程序页。  
  
## <a name="application-pages"></a>应用程序页  
 应用程序页是在服务器上，所有站点共享，而站点页面是特定于一个站点。 有关详细信息， [SharePoint 页类型](http://go.microsoft.com/fwlink/?LinkID=211584)。  
  
 默认情况下，当你创建一个 SharePoint 站点时，显示的页面的大部分都是网站页。 网站页面可以添加到 SharePoint 页库。 通过使用 SharePoint 设计器等工具，用户可以自定义网站页。 网站页面也可以承载功能，如动态 Web 部件和 Web 部件区域。  
  
 应用程序页不能执行这些操作。 但是对应用程序页进行页后，可以创建如果你想页后，可以包含自定义代码的最佳类型。 尽管可以将自定义代码添加到站点页面中，在代码停止运行时在用户通过使用 SharePoint 设计器等工具自定义页。  
  
> [!NOTE]  
>  Visual Studio 不提供帮助你的模板创建为 SharePoint 站点的站点页面。 有关详细信息，请参阅[SharePoint 页类型](http://go.microsoft.com/fwlink/?LinkID=211584)。  
  
## <a name="creating-an-application-page"></a>创建应用程序页  
 若要创建的应用程序页，添加**应用程序页**到 SharePoint 项目项。 在你创建的应用程序页，Visual Studio 将添加到你的项目的以下文件夹：  
  
|文件夹|描述|  
|------------|-----------------|  
|布局|映射到 SharePoint 文件系统的 _layouts 虚拟目录。|  
|布局子文件夹|包含构成应用程序页上的文件。 默认情况下，此文件夹具有与你的项目相同的名称。 你可以在任何时候重命名此文件夹。 运行项目时，Visual Studio 将部署到 SharePoint 文件系统的 _layouts 虚拟目录的此文件夹。|  
  
 Visual Studio 将添加到你的项目的以下文件：  
  
|文件|描述|  
|----------|-----------------|  
|ASP.NET 页文件 (.aspx)|包含定义页的 XML 标记。|  
|应用程序页代码文件|包含应用程序页背后的代码。 添加代码来处理对此文件的事件。|  
|应用程序页设计器代码文件|包含设计器所生成的代码。 不要直接编辑此文件。|  
  
## <a name="designing-and-debugging-an-application-page"></a>设计和调试的应用程序页  
 通过使用 Visual Studio 中的设计器视图中设计的应用程序页的内容。 当在你的项目中打开应用程序页上，将显示此设计器 (通过双击它或打开其快捷菜单，然后选择**打开**)，然后选择**设计**底部的按钮编辑器。  
  
> [!NOTE]  
>  你可以设计页仅在**源**的设计器视图。 **设计**为应用程序页禁用设计器的视图。  
  
 正如你将调试其他 Visual Studio 中的 SharePoint 项目项，你可以调试的应用程序页。 当你启动 Visual Studio 调试器时，Visual Studio 将打开 SharePoint 站点。  
  
 若要查看应用程序页上，您必须手动导航到应用程序页的位置 (例如： http://*Server_Name*/_layouts/*文件的内容*/ApplicationPage1.aspx)。  
  
 有关如何调试 SharePoint 项目的详细信息，请参阅[疑难解答 SharePoint 解决方案](../sharepoint/troubleshooting-sharepoint-solutions.md)。  
  
## <a name="choosing-a-master-page"></a>选择母版页  
 默认情况下，**应用程序页**项引用用来调试你的项目的站点的主页面。 页名为 v4.master，并且你可以找到它列入**母版页样式库**的 SharePoint 站点。  
  
 你可以显式更改哪些母版页由应用程序页上通过设置`MasterPageFile`的应用程序的属性`Page`元素。 (例如： `MasterPageFile="~/_layouts/applicationv4.master"`)。 事实上，如果 SharePoint 服务器上未启用动态母版页，则必须设置此属性。 有关在 SharePoint 中的主控页的详细信息，请参阅[母版页](http://go.microsoft.com/fwlink/?LinkID=169281)。  
  
## <a name="see-also"></a>另请参阅  
 [深度中的 SharePoint Foundation 开发](http://go.microsoft.com/fwlink/?LinkID=182103)   
 [ASP.NET 概述](/aspnet/overview)   
 [ASP.NET 网页](/aspnet/web-pages/index)   
  
  