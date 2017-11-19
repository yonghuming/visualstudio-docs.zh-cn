---
title: "为 SharePoint 创建页 |Microsoft 文档"
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
helpviewer_keywords:
- SharePoint development in Visual Studio, master pages
- SharePoint development in Visual Studio, page layouts
- SharePoint development in Visual Studio, content pages
- master pages[SharePoint development in Visual Studio], designing
- content pages[SharePoint development in Visual Studio], designing
- page layouts[SharePoint development in Visual Studio], designing
ms.assetid: 57678ed1-841f-45de-a1d3-5f9e233bf3ce
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bef1fce26bbd9ea57073273f462ec484a46a647b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-pages-for-sharepoint"></a>为 SharePoint 创建页
  你可以创建应用程序页、 网站页、 母版页和页面布局为 SharePoint 站点。  
  
 可以通过使用 Visual Studio 中的模板来创建应用程序页。 通过使用 SharePoint Designer 中创建网站页、 母版页和页面布局。 然后，你可以将这些页面导入 Visual Studio 的 SharePoint 项目中使用它们。  
  
 你可以通过使用级联样式表、 ECMAScript 和主题来修改的外观和行为的页数。  
  
## <a name="types-of-sharepoint-pages"></a>类型的 SharePoint 页  
 下表介绍四种主要类型的 SharePoint 站点包含的页。  
  
|页类型|描述|  
|---------------|-----------------|  
|应用程序页|如果想页后，可以包含自定义代码，或者你想要在多个站点之间共享的页，请创建一个应用程序页面。 否则，站点页可能是最佳选择。|  
|网站页|创建网站页面，如果你想要执行任何以下任务：<br /><br /> -将页添加到 SharePoint 库。<br />-启用对动态 Web 部件和 Web 部件区域等主机功能页。<br />-使用户能够通过使用 SharePoint Designer 自定义。<br /><br /> 如果你想页后，可以包含自定义代码，则不创建站点页。 尽管可以将自定义代码添加到站点页面中，在代码停止运行时在用户通过使用 SharePoint Designer 自定义页。|  
|母版页|创建 master 页上，如果你想要定义站点页面的通用结构和应用程序页。|  
|页面布局|页面布局是特定于[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]并且使你可以进一步定义站点页和应用程序页的通用结构。|  
  
 每种类型的页的概述，请参阅[构建基块： 页和用户界面](http://go.microsoft.com/fwlink/?LinkID=182095)，和[页面布局和母版页](http://go.microsoft.com/fwlink/?LinkID=182096)。  
  
## <a name="creating-application-pages"></a>创建应用程序页  
 可以通过添加在 Visual Studio 中创建应用程序页**应用程序页**到 SharePoint 项目项。 可以将控件添加到页上，然后通过将代码添加处理控件事件。  
  
 你可以在页的代码文件中设置断点、 启动调试器，和测试本地 SharePoint 站点上的页面而不执行任何其他配置步骤。 有关详细信息，请参阅[for SharePoint 创建应用程序页](../sharepoint/creating-application-pages-for-sharepoint.md)。  
  
## <a name="creating-site-pages-master-pages-and-page-layouts"></a>创建网站页、 母版页和页面布局  
 可以通过使用 SharePoint Designer 中创建网站页、 母版页和页面布局。 然后，你可以将这些页面导入 Visual Studio。 如果你想要利用的部署或 Visual Studio 中提供的源代码管理功能，导入页面。 有关详细信息，请参阅[从现有的 SharePoint 网站导入项](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)。  
  
 因为很难修改这些页，将其导入后，应在导入之前设计这些页面。  
  
## <a name="creating-cascading-style-sheets-ecmascript-and-themes"></a>创建级联样式表，此情况下和主题  
 Visual Studio 不提供开发级联样式表 (CSS)、 ECMAScript （JavaScript、 JScript） 或 SharePoint 站点的主题文件的模板。 你可以使用 SharePoint SDK 中提供的指南或通过使用 SharePoint 设计器等工具创建这些文件。  
  
 可以直接将这些文件添加到你的解决方案或将其导入。 在任一情况下，你必须创建对于你添加的每个项相应映射的文件夹。 有关如何创建一个映射的文件夹的详细信息，请参阅[如何： 添加和移除映射文件夹](../sharepoint/how-to-add-and-remove-mapped-folders.md)。  
  
 有关创建级联样式表的详细信息，请参阅[级联样式表类中的使用情况 SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkID=182098)。 有关创建 SharePoint 解决方案的 JavaScript 和 JScript 文件的详细信息，请参阅[设置向上基本 ASPX 页 ECMAScript](http://go.microsoft.com/fwlink/?LinkID=182099)。 有关主题的详细信息，请参阅[构建基块： 页和用户界面](http://go.microsoft.com/fwlink/?LinkID=182095)。  
  
## <a name="related-topics"></a>相关主题  
  
|标题|描述|  
|-----------|-----------------|  
|[为 SharePoint 创建应用程序页](../sharepoint/creating-application-pages-for-sharepoint.md)|描述如何添加应用程序页： 与 SharePoint 母版页合并的.aspx 内容。|  
|[如何：创建应用程序页](../sharepoint/how-to-create-an-application-page.md)|演示如何创建在 SharePoint 站点运行的 ASP.NET 页。|  
|[演练：创建 SharePoint 应用程序页](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|演示如何设计和调试 SharePoint 站点的 ASP.NET 网页。|  
  
  