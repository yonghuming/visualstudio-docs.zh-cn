---
title: "为 SharePoint 创建 Web 部件 | Microsoft Docs"
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
  - "Microsoft.SharePoint.WebControls.DateTimeControl"
  - "Microsoft.SharePoint.WebControls.CssLink"
  - "Microsoft.SharePoint.WebControls.RssLink"
  - "Microsoft.SharePoint.WebControls.Theme"
  - "Microsoft.SharePoint.WebControls.AspMenu"
  - "Microsoft.SharePoint.WebControls.ListProperty"
  - "Microsoft.SharePoint.WebControls.ProjectProperty"
  - "Microsoft.SharePoint.WebControls.FormsDigest"
  - "Microsoft.SharePoint.WebControls.ScriptLink"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 开发, Web 部件"
  - "Web 部件 [Visual Studio 中的 SharePoint 开发], 设计"
ms.assetid: a6349e85-45cf-4766-b856-e25c9f1ffd34
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# 为 SharePoint 创建 Web 部件
  利用 Web 部件，可通过使用浏览器直接修改 SharePoint 站点页面的内容、外观和行为。  Web 部件是在 Web 部件页内部运行的服务器端控件:它们是在 SharePoint 站点上显示的页的生成块。  请参见 [Building Block: Web Parts](http://go.microsoft.com/fwlink/?LinkID=182097)（生成块：Web 部件）。  
  
 您可以使用 Visual Studio 上的模板在 SharePoint 站点上创建和调试 Web 部件。  
  
## 在 Visual Studio 中创建 Web 部件  
 可以通过向任何 SharePoint 项目添加“Web 部件”项创建 Web 部件。  您可以使用沙盒解决方案或场解决方案中的**“Web 部件”**项。  
  
 如果想使用设计器直观地设计 Web 部件，请创建“可视 Web 部件”项目或向任何 SharePoint 项目添加“可视 Web 部件”项。  您只能使用场解决方案中的**“可视 Web 部件”**项。  
  
### Web 部件项  
 “Web 部件”项提供了可用于设计 SharePoint 站点的 Web 部件的文件。  添加“Web 部件”项后，Visual Studio 将在您的项目中创建一个文件夹，然后向该文件夹中添加几个文件。  下表介绍每个文件。  
  
|文件|描述|  
|--------|--------|  
|Elements.xml|包含项目中的功能定义文件用来部署 Web 部件的信息。|  
|.webpart 文件|提供 SharePoint 显示 Web 部件库中的 Web 部件所需的信息。|  
|代码文件|包含向 Web 部件添加控件并在该 Web 部件中生成自定义内容的方法。|  
  
 有关详细信息，请参阅[如何：创建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part.md)。  
  
### 可视 Web 部件项  
 可视 Web 部件是使用 Visual Studio 中的 Visual Web Developer 设计器创建的 Web 部件。  请参见 [Visual Studio Web 开发环境内容映射](http://msdn.microsoft.com/zh-cn/9c31f93b-c8fb-4599-9b14-6194ec8c7539)。  
  
 可视 Web 部件功能和其他 Web 部件相同。  要将例如按钮和文本框的控件添加到 Web 部件，请将代码添加到 XML 文件中。  但是，您可以通过从 Visual Studio“工具箱”拖动或复制控件到 web 部件，将控件添加到可视 web 部件。  然后设计器生成 XML 文件所需的代码。  请参见 [如何：使用设计器创建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)。  
  
## SharePoint 控件  
 Visual Studio 会提供用于创建 SharePoint 页（如应用程序页）的一些控件。  这些控件显示在“SharePoint 控件”下的“工具箱”中。  这些控件的功能派生于 [Microsoft.SharePoint.WebControls](http://go.microsoft.com/fwlink/?LinkId=235315) 命名空间，该命名空间包含 SharePoint 站点和列表页上使用的 ASP.NET 服务器控件。  
  
|控件名称|描述|  
|----------|--------|  
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|插入 ASP 菜单。  有关详细信息，请参见[Menu Control Overview](http://go.microsoft.com/fwlink/?LinkId=235316)（菜单控件概述）。|  
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|将 **LINK** 元素插入 .aspx 页中，然后应用一个或多个由 **CssRegistration** 定义的外部样式表。|  
|[DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|将 DateTime 控件插入 .aspx 页中。|  
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|将安全验证插入 .aspx 页中|  
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|返回指定列表的属性。|  
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|返回当前网站的全局属性。|  
|[RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|将 RSS 源的链接插入 .aspx 页中。|  
|[ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|提供在页上注册资源的属性和方法（如脚本）以便能在呈现页时请求。|  
|[Theme](http://go.microsoft.com/fwlink/?LinkId=235314)（主题）|应用主题到 .aspx 页。|  
  
## 调试 Web 部件  
 您可以调试包含 Web 部件的 SharePoint 项目，就像调试其他 Visual Studio 项目一样。  当您启动 Visual Studio 调试器时，Visual Studio 将打开 SharePoint 站点。  
  
 若要开始调试代码，请在 SharePoint 中将 Web 部件添加到 Web 部件页。  
  
 有关如何调试 SharePoint 项目的更多信息，请参见[SharePoint 解决方案疑难解答](../sharepoint/troubleshooting-sharepoint-solutions.md)。  
  
## 可视 Web 部件限制  
 在 Visual Studio 里启动后，您可以将可视 Web 部件添加到沙盒 SharePoint 解决方案和场解决方案。  但是，可视 web 部件具有以下限制：  
  
-   可视 Web 部件不支持可替换参数。  有关详细信息，请参阅[可替换参数](../sharepoint/replaceable-parameters.md)。  
  
-   用户控件或可视 Web 部件无法拖放到或复制到可视 Web 部件上。  此操作会生成错误。  
  
-   可视 Web 部件不直接支持 SharePoint 服务器标记，如 $SPUrl。  有关详细信息，请参见主题 [SharePoint 解决方案疑难解答](../sharepoint/troubleshooting-sharepoint-solutions.md) 中的“沙盒可视 Web 部件中的标记限制”。  
  
-   沙盒解决方法中的可视 Web 部件偶尔会发生错误，“已拒绝沙盒代码执行请求，因为沙盒代码托管服务太忙，无法处理该请求”。有关此错误的更多信息，请参见 [SharePoint Developer Team Blog](http://go.microsoft.com/fwlink/?LinkId=225932)（SharePoint 开发人员团队博客）中的这篇文章。  
  
-   Visual Studio 不支持服务器端 JavaScript 调试，但是支持客户端 JavaScript 调试。  
  
     虽然您可以将内联 JavaScript 添加到服务器侧的标记文件，但添加到标记的断点仍然不支持调试。  若要调试 JavaScript，请在标记文件中引用外部 JavaScript 文件，然后在 JavaScript 文件中设置断点。  
  
-   调试内联 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 代码必须在生成的代码文件中完成，而不是在标记文件中。  
  
-   可视 Web 部件不支持使用 `<@ Assembly Src=` 指令。  
  
-   SharePoint 沙盒环境不支持 SharePoint Web 控件以及一些 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 控件。  如果对沙盒解决方案中的可视 web 部件使用不支持的控件，则显示错误：“类型或命名空间名称‘主题’在命名空间‘Microsoft.SharePoint.WebControls'中不存在”。  
  
 有关沙盒解决方案的更多信息，请参见 [沙盒解决方案与场解决方案之间的差异](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)。  
  
## 创建基于较旧样式的 SharePoint 的 Web 部件  
 使用 Visual Studio 中的模板，可以为 SharePoint 创建自定义 [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] Web 部件。  [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] Web 部件构建在 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Web 部件基础结构之上，是新项目的推荐类型。  
  
 在极少数情况下，您可能需要使用较旧样式的基于 SharePoint 的 Web 部件来创建 Web 部件。  可以使用 Visual Studio 创建这些类型的 Web 部件，但是 Visual Studio 不提供专门用来帮助创建这些部件的任何模板。  
  
 有关何时需要创建基于 SharePoint 的较旧样式 Web 部件的更多信息，请参见 [Web Part Infrastructure in Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=169290)（Windows SharePoint Services 中的 Web 部件基础结构）。  有关如何使用基于较旧样式 SharePoint 的 Web 部件创建 Web 部件的更多信息，请参见 [Walkthrough Creating a Basic SharePoint Web Part](http://go.microsoft.com/fwlink/?LinkId=169288)（演练：创建基本 SharePoint Web 部件）。  
  
## 相关主题  
  
|标题|描述|  
|--------|--------|  
|[如何：创建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part.md)|演示如何为 SharePoint 页创建 Web 部件。|  
|[如何：使用设计器创建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|演示如何使用可视设计图面为 SharePoint 创建 Web 部件。|  
|[如何：为 SharePoint 应用程序页或 Web 部件创建用户控件](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|演示如何创建可由在 SharePoint 中运行的应用程序页和 Web 部件使用的自定义可重用控件。|  
|[演练：为 SharePoint 创建 Web 部件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|说明如何为 SharePoint 设计 Web 部件。|  
|[演练：使用设计器为 SharePoint 创建 Web 部件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|介绍如何通过将控件拖动到可视设计图面来为 SharePoint 设计 Web 部件。|  
|[演练：创建显示 SharePoint OData 的 Silverlight Web 部件](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|描述如何为承载 Silverlight 应用程序和显示 SharePoint 列表中的数据设计 web 部件。|  
|[使用 Visual Web Developer](http://msdn.microsoft.com/zh-cn/9c31f93b-c8fb-4599-9b14-6194ec8c7539)|说明如何使用在项目中打开网页时出现的设计器。|  
  
  