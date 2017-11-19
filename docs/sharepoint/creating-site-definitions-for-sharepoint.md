---
title: "创建 SharePoint 站点定义 |Microsoft 文档"
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
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
ms.assetid: 83db570d-6b9f-4dab-9e71-db41f17b987a
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a4a7c002bd17da5f693955a82ab2e74bf65dc0cd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-site-definitions-for-sharepoint"></a>创建 SharePoint 网站定义
  中的 SharePoint 网站定义项目[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]允许你创建*站点定义*，它用作新的 SharePoint 站点的基础。 这些定义不仅确定的外观和行为的 SharePoint 站点，但还自己的默认内容和功能。 在定义中，您可以放入预配置的列表、 内容类型、 事件接收器、 图像和其他项。 例如 SharePoint 包含某些网站定义（如 BLOG）。 在创建了基于博客站点定义的网站时，网站包含列表、 Web 部件和博客网站所需的其他项。  
  
 有关站点定义的详细信息，请参阅[站点模板和定义](http://go.microsoft.com/fwlink/?LinkId=179134)。  
  
## <a name="site-definition-projects"></a>网站定义项目  
 站点中的定义项目[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]提供仅将 SharePoint 站点需要的基本文件; 它们不提供任何默认功能。 你必须添加文件和内容，以提供所需的功能。 创建并添加所需的文件，可以手动，生成的站点。  
  
## <a name="feature-stapling"></a>功能附加  
 创建站点定义中的一个好处[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]是时会自动使用*功能附加*。 功能附加将附加到的站点定义而不是在站点定义本身中嵌入其功能的一项功能。 这样做可让你将功能添加到而无需修改原始的站点定义中使用的站点定义创建的任何站点。 有关详细信息，请参阅[功能附加](http://go.microsoft.com/fwlink/?LinkID=119283)。  
  
## <a name="site-definition-project-components"></a>网站定义项目组件  
 当你创建网站定义解决方案时，将以下默认文件添加到其**SiteDefinition**节点。  
  
|文件名|描述|  
|---------------|-----------------|  
|default.aspx|新的 SharePoint 站点默认 ASPX 主页。|  
|Onet.xml|指定新的站点的配置、 站点定义模板，默认行为的组件。 这些设置可以包括属性的内容类型启用，则默认列表视图中，文档模板文件，例如和 Web 部件包括与该站点。 默认情况下，`Modules`部分列出了要添加到 SharePoint 站点，如何配置这些设置的文件。|  
|webtemp_*SiteDefinitionName*.xml|指定出现在站点定义配置**模板选择**部分**新建 SharePoint 网站**页。|  
  
 默认情况下，所有站点定义都存储在*驱动器：*\program Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates 文件夹。 每个站点定义都包含其自己的子文件夹。  
  
## <a name="related-topics"></a>相关主题  
  
|标题|描述|  
|-----------|-----------------|  
|[演练：创建基本站点定义项目](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|将引导你逐步完成基本网站定义项目中创建[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。|  
|[如何： 创建自定义站点定义和配置](http://go.microsoft.com/fwlink/?LinkId=183309)|描述如何在 SharePoint 中创建自定义站点定义，通过复制现有的站点定义，然后对副本进行修改。|  
|[WebTemp.xml](http://go.microsoft.com/fwlink/?LinkId=183310)|描述指定的站点定义中提供的原始文件**模板选择**部分**新建 SharePoint 网站**页。|  
|[本地化 SharePoint 解决方案](../sharepoint/localizing-sharepoint-solutions.md)|描述如何准备的共用的 SharePoint 解决方案。|  
|[为 SharePoint 创建 Web 部件](../sharepoint/creating-web-parts-for-sharepoint.md)|描述如何创建用户可以修改 SharePoint 页的部件。|  
|[为 Web 部件或应用程序页创建可重用控件](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|描述如何创建在应用程序页和 Web 部件中运行的可重用控件。|  
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|介绍如何使用你的项目中打开 Web 页时显示的设计器。|  
|[ASP.NET Web 页概述](http://go.microsoft.com/fwlink/?LinkId=178726)|提供有关的结构的常规信息[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]Web 页面，通过处理页的方式[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]，以及如何[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]页将显示符合 XHTML 标准的标记。|  
|[ASP.NET Web 页语法](http://go.microsoft.com/fwlink/?LinkId=178727)|描述构成 ASP.NET 页的标记元素。|  
|[编程 ASP.NET 网页](http://go.microsoft.com/fwlink/?LinkId=178728)|提供有关如何创建事件处理程序中的信息[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]页以及如何使用客户端脚本。|  
|[在 Windows SharePoint Services 中进行编程](http://go.microsoft.com/fwlink/?LinkId=178729)|介绍如何使用中提供的托管的对象模型[!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)]。|  
  
## <a name="see-also"></a>另请参阅  
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  