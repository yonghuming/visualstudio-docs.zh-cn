---
title: "为 SharePoint 创建 Web 部件 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Microsoft.SharePoint.WebControls.DateTimeControl
- Microsoft.SharePoint.WebControls.CssLink
- Microsoft.SharePoint.WebControls.RssLink
- Microsoft.SharePoint.WebControls.Theme
- Microsoft.SharePoint.WebControls.AspMenu
- Microsoft.SharePoint.WebControls.ListProperty
- Microsoft.SharePoint.WebControls.ProjectProperty
- Microsoft.SharePoint.WebControls.FormsDigest
- Microsoft.SharePoint.WebControls.ScriptLink
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web Parts
- Web Parts [SharePoint development in Visual Studio], designing
ms.assetid: a6349e85-45cf-4766-b856-e25c9f1ffd34
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5bba3f2e5f645b6b97fb43b22e7dfc1028a01ab0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-web-parts-for-sharepoint"></a>为 SharePoint 创建 Web 部件
  通过使用 web 部件，可以使用浏览器来修改内容、 外观和行为的 SharePoint 站点的页。 Web 部件是在 web 部件页内运行的服务器端控件： 它们是在 SharePoint 站点显示的页的构建基块。 请参阅[构建基块： Web 部件](http://go.microsoft.com/fwlink/?LinkID=182097)。  
  
 你可以创建和使用模板从 Visual Studio 中调试 SharePoint 站点上的 web 部件。  
  
## <a name="creating-a-web-part-in-visual-studio"></a>在 Visual Studio 中创建 Web 部件  
 通过添加创建 web 部件**Web 部件**到任何 SharePoint 项目项。 你可以使用**Web 部件**沙盒解决方案或场解决方案中的项。  
  
 如果你想要通过使用设计器中以可视方式设计 web 部件，创建**可视 Web 部件**项目或添加**可视 Web 部件**到任何 SharePoint 项目项。 你可以使用**可视 Web 部件**场解决方案中的项。  
  
### <a name="web-part-item"></a>Web 部件项目  
 A **Web 部件**项提供了可用于设计为 SharePoint 站点的 web 部件的文件。 当你将添加**Web 部件**项、 Visual Studio 项目中创建一个文件夹，然后将多个文件添加到的文件夹。 下表介绍每个文件。  
  
|文件|描述|  
|----------|-----------------|  
|Elements.xml|包含你的项目中的功能定义文件用于部署 web 部件的信息。|  
|.webpart 文件|提供 SharePoint 需要在 web 部件库中显示 web 部件的信息。|  
|代码文件|包含用于将控件添加到 web 部件以及生成 web 部件中的自定义内容的方法。|  
  
 有关详细信息，请参阅[如何： 创建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part.md)。  
  
### <a name="visual-web-part-item"></a>可视 Web 部件项目  
 可视 web 部件是通过使用 Visual Studio 中 Visual Web Developer 设计器创建的 web 部件。 可视 web 部件的函数与任何其他 web 部件相同。 若要添加到 web 部件控件，如按钮和文本框中，你将代码添加到 XML 文件。 但是，你将控件添加到可视 web 部件拖动或从 Visual Studio 将其复制到 web 部件**工具箱**。 设计器然后生成 XML 文件中的所需的代码。 请参阅[如何： 使用设计器创建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)。  
  
## <a name="sharepoint-controls"></a>SharePoint 控件  
 Visual Studio 提供用于创建 SharePoint 页面，例如应用程序页的某些控件。 这些控件出现在**工具箱**下**SharePoint 控件**。 这些控件的功能派生自[Microsoft.SharePoint.WebControls](http://go.microsoft.com/fwlink/?LinkId=235315)命名空间，其中包含 SharePoint 站点和列表页面所使用的 ASP.NET 服务器控件。  
  
|控件名称|描述|  
|------------------|-----------------|  
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|将插入一个 ASP 菜单。 有关详细信息，请参阅[菜单控件概述](http://go.microsoft.com/fwlink/?LinkId=235316)。|  
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|将插入**链接**元素插入的.aspx 页，并将应用所定义的一个或多个外部样式表**CssRegistration**。|  
|[DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|将 DateTime 控件插入到的.aspx 页。|  
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|安全验证插入的.aspx 页|  
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|返回指定列表中的一个属性。|  
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|返回当前网站的全局属性。|  
|[RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|将插入 rss 源到.aspx 页的链接。|  
|[ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|提供用于注册资源，如脚本，在页面上，以便他们可以请求呈现页时属性和方法。|  
|[主题](http://go.microsoft.com/fwlink/?LinkId=235314)|将主题应用于的.aspx 页。|  
  
## <a name="debugging-a-web-part"></a>调试 Web 部件  
 你可以调试一个包含 web 部件，正如你将调试其他 Visual Studio 项目的 SharePoint 项目。 当你启动 Visual Studio 调试器时，Visual Studio 将打开 SharePoint 站点。  
  
 若要开始调试代码，将添加到 SharePoint 中的 web 部件页的 web 部件。  
  
 有关如何调试 SharePoint 项目的详细信息，请参阅[疑难解答 SharePoint 解决方案](../sharepoint/troubleshooting-sharepoint-solutions.md)。  
  
## <a name="visual-web-part-limitations"></a>可视 Web 部件限制  
 启动 Visual Studio 中，可以将可视 web 部件添加到沙盒 SharePoint 解决方案和场解决方案。 但是，可视 web 部件具有以下限制：  
  
-   可视 web 部件不支持可替换参数。 有关详细信息，请参阅[可替换参数](../sharepoint/replaceable-parameters.md)。  
  
-   无法拖放和删除或复制到的可视 web 部件用户控件或可视 web 部件。 此操作会导致生成错误。  
  
-   可视 web 部件不直接支持 SharePoint server 标记，例如 $SPUrl。 有关详细信息，请参阅"令牌限制在沙盒可视 Web 部件"主题[疑难解答 SharePoint 解决方案](../sharepoint/troubleshooting-sharepoint-solutions.md)。  
  
-   沙盒解决方案中的可视 web 部件偶尔遇到错误，即"沙盒代码执行请求已被拒绝，因为沙盒代码主机服务已太忙而无法处理该请求。" 有关此错误的详细信息，请参阅此文章中的[SharePoint 开发人员团队博客](http://go.microsoft.com/fwlink/?LinkId=225932)。  
  
-   服务器端 JavaScript 调试不支持在 Visual Studio 中，但客户端 JavaScript 调试支持。  
  
     不过你可以将内联 JavaScript 添加到服务器端标记文件中，不支持添加到标记的断点的调试。 若要调试 JavaScript，引用外部 JavaScript 文件中的标记文件，然后再设置 JavaScript 文件中的断点。  
  
-   调试内联[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]代码必须在标记文件中而不是生成的代码文件中。  
  
-   可视 web 部件不支持使用`<@ Assembly Src=`指令。  
  
-   SharePoint web 控件和一些[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]控件不支持在 SharePoint 沙盒环境中。 如果使用不受支持的控件的可视 web 部件在沙盒解决方案中，该错误，将显示"的类型或命名空间名称主题中的命名空间 Microsoft.SharePoint.WebControls 不存在"。  
  
 有关沙盒解决方案的详细信息，请参阅[差异之间沙盒解决方案和场解决方案](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)。  
  
## <a name="creating-older-style-sharepoint-based-web-parts"></a>创建旧样式的基于 SharePoint Web 部件  
 你可以使用在 Visual Studio 中的模板来创建自定义[!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)]for SharePoint web 部件。 [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)]均构建在 web 部件之上[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]web 部件基础结构，并且为新项目的建议的类型。  
  
 在极少数情况下，你可能需要使用较旧的形式的基于 SharePoint web 部件创建 web 部件。 你可以使用 Visual Studio 创建这些类型的 web 部件，但 Visual Studio 不提供任何专用于帮助你创建它们的模板。  
  
 有关当你可能想要创建较旧的形式的基于 SharePoint web 部件的详细信息，请参阅[Web 部件中 Windows SharePoint Services 的基础结构](http://go.microsoft.com/fwlink/?LinkId=169290)。 有关如何使用旧样式的基于 SharePoint web 部件创建 web 部件的详细信息，请参阅[创建基本的 SharePoint Web 部件的演练](http://go.microsoft.com/fwlink/?LinkId=169288)。  
  
## <a name="related-topics"></a>相关主题  
  
|标题|描述|  
|-----------|-----------------|  
|[如何：创建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part.md)|演示如何创建 web 部件的 SharePoint 页。|  
|[如何：使用设计器创建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|演示如何使用一个可视化设计图面为 SharePoint 创建 web 部件。|  
|[如何：为 SharePoint 应用程序页或 Web 部件创建用户控件](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|演示如何创建可由应用程序页和 SharePoint 中运行的 web 部件使用的自定义的可重用控件。|  
|[演练：为 SharePoint 创建 Web 部件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|描述如何设计为 SharePoint web 部件。|  
|[演练：使用设计器为 SharePoint 创建 Web 部件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|描述如何通过将控件拖动到可视化设计图面中设计为 SharePoint web 部件。|  
|[演练：创建显示 SharePoint OData 的 Silverlight Web 部件](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|描述如何设计承载 Silverlight 应用程序和 SharePoint 列表中显示的数据的 sharepoint web 部件。|  
  
  