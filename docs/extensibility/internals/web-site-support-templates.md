---
title: "网站支持模板 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4e3d64f77064c04e131853786495c921711f2d0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="web-site-support-templates"></a>网站支持模板
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]网站项目和项模板提供了无需从头开始创建新网站项目和项来加快开发过程的可重用和可自定义网站项目和项存根。 有关详细信息[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]模板，请参阅[创建项目和项模板](../../ide/creating-project-and-item-templates.md)。  
  
## <a name="project-template-folder"></a>项目模板文件夹  
 Web 项目模板模板通常安装在 [*Visual Studio 安装路径*] \Common7\IDE\ProjectTemplates\Web\\，每个命名 web 编程语言的子文件夹中。  
  
## <a name="project-file"></a>项目文件  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE) 作为一种方法将模板映射到正确的项目类型需要项目文件扩展名的文件。 Web 项目没有项目文件，因为 dummy 项目文件扩展名.webproj 注册为支持此功能。  
  
 （可选） 的语言名称字符串可以添加到模板，以使 Web 项目系统，在中设置语言默认**添加新项**对话框中的项在基于的模板。 字符串必须是该文件的第一行，并且必须与在 AddItemLanguageName 下注册 Intellisense 引擎注册中的名称和在项目 Subtype(VsTemplate) 下注册的名称匹配。 有关详细信息，请参阅[网站支持属性](../../extensibility/internals/web-site-support-attributes.md)。  
  
 如果字符串不存在，Web 项目系统将尝试确定基于项目模板模板添加到 Web 项目的页的语言属性和文件扩展的默认语言。  
  
## <a name="project-templates"></a>项目模板  
 网站项目模板用于生成在响应中的新网站**新网站**命令**文件**菜单。 当前支持三个网站项目类型：  
  
-   空网站项目  
  
-   网站项目  
  
-   Web 服务项目  
  
### <a name="empty-web-site-projects"></a>空网站项目  
 这些文件创建新的空网站以响应**空网站**命令，指向之后，将可用**新网站**上**文件**菜单：  
  
-   EmptyWeb.vstemplate  
  
     模板文件，以指导创建新的空网站。  
  
-   EmptyWeb.webproj  
  
     此文件是项目模板系统的项目。 满足 EmptyWeb.vstemplate 文件中的项目文件引用。  
  
### <a name="web-site-projects"></a>网站项目  
 这些文件创建新网站以响应**ASP.NET 网站**命令，指向之后，将可用**新网站**上**文件**菜单：  
  
-   Default.aspx  
  
     默认值主页的为新网站。 Language 特性指定的代码隐藏语言，并同特性指定包含关联的这一页的代码隐藏代码的依赖文件。  
  
-   Default.aspx。*扩展*  
  
     包含默认主页上的代码隐藏代码的依赖文件。 代码隐藏语言确定*扩展*此文件。  
  
-   web.config  
  
     根 web.site 配置文件。  
  
-   WebApplication.vstemplate  
  
     模板文件，并强制创建 App_Data 文件夹将确定网站解决方案的内容。  
  
-   WebApplication.webproj  
  
     此文件是项目模板系统的项目。 满足 WebApplication.vstemplate 文件中的项目文件引用。  
  
### <a name="web-service-projects"></a>Web 服务项目  
 这些文件创建新网站以响应**ASP.NET Web 服务**命令指向后即可使用**新网站**上**文件**菜单：  
  
-   Service.asmx  
  
     新的 Web 服务的 HTML 页。 Language 特性指定的代码隐藏语言，和代码隐藏文件特性指定包含与此服务关联的代码隐藏代码的依赖文件。  
  
-   服务。 *扩展*  
  
     实现服务类中的依赖文件。 代码隐藏语言确定*扩展*此文件。  
  
-   web.config  
  
-   根 web.site 配置文件。  
  
-   WebService.vstemplate  
  
     模板文件，并强制创建的 App_Data 和 App_Code 文件夹将确定网站解决方案的内容。 该服务。*扩展*文件复制到 App_Code 文件夹。  
  
-   WebService.webproj  
  
     此文件是项目模板系统的项目。 满足 WebService.vstemplate 文件中的项目文件引用。  
  
## <a name="project-item-template-folder"></a>项目项模板文件夹  
 Web 项目项模板模板通常安装在 [*Visual Studio 安装路径*] \Common7\IDE\ItemTemplates\Web\\，每个命名其 web 编程语言的子文件夹中。  
  
## <a name="project-item-templates"></a>项目项模板  
 网站项目项模板用于将新的 Web 页添加到响应中的 Web 站点**添加现有项**命令。 当前支持这些种类的网页：  
  
-   新类  
  
-   新的 HTML 页  
  
-   新的 Web 窗体  
  
-   新的母版页  
  
### <a name="new-class"></a>新类  
 此模板创建一个新的源文件用于定义在响应中的空类**添加新类**命令。  
  
-   类。 *扩展*  
  
     实现空类的源文件。 代码隐藏语言确定*扩展*此文件。  
  
-   Class.vstemplate  
  
     模板文件，以创建源文件，并确定其内容。  
  
### <a name="new-html-page"></a>新的 HTML 页  
 此模板创建一个新的 Web 页以响应**添加新的 HTML 页**命令。  
  
-   HTMLPage.htm  
  
     Web 页面的起始内容。 此网页通常具有任何关联的代码隐藏依赖文件。 若要创建智能页关联的代码隐藏文件，请改为使用 Web 窗体模板。  
  
-   HTMLPage.vstemplate  
  
     模板文件，以创建网页并确定其内容。  
  
### <a name="new-webform"></a>新的 web 窗体  
 此模板创建一个新的智能 Web 页以响应**添加新的 Web 窗体**命令。  
  
 若要创建依赖的代码隐藏的源文件，请选择**将代码放在单独的文件**。 否则单个网页将创建具有空的脚本块，但不\<%页 %> 指令挂接依赖文件。  
  
 若要创建所选的母版页的内容页，选择**选择母版页**。  
  
-   WebForm.aspx  
  
     Web 页面的起始内容。 此 Web 页面已没有关联的代码隐藏依赖文件。  
  
-   WebForm_cb.aspx  
  
     Web 页面的起始内容。 此 Web 页面都有关联的代码隐藏依赖文件。  
  
-   代码隐藏。 *扩展*  
  
     实现 web 窗体类中的依赖文件。 代码隐藏语言确定*扩展*此文件。  
  
-   ContentPage.aspx  
  
     作为内容页 Web 页面的起始内容。 此 Web 页面已没有关联的代码隐藏依赖文件。  
  
-   ContentPage_cb.aspx  
  
     作为内容页 Web 页面的起始内容。 此 Web 页面都有关联的代码隐藏依赖文件。  
  
-   WebForm.vstemplate  
  
     确定新的 web 页面，其依赖文件的内容，如果任何模板文件。  
  
### <a name="new-master-page"></a>新建母版页  
 此模板创建一个新的主页以响应**添加新的母版页**命令。  
  
 若要创建依赖的代码隐藏的源文件，请选择**将代码放在单独的文件**。 否则单个网页将创建具有空的脚本块，但不\<%页 %> 指令挂接依赖文件。  
  
-   MasterPage.master  
  
     主页面的起始内容。 此母版页具有任何关联的代码隐藏依赖文件。  
  
-   MasterPage_cb.master  
  
     主页面的起始内容。 此主页都有关联的代码隐藏依赖文件。  
  
-   代码隐藏。*扩展*  
  
     实现母版页类中的依赖文件。 代码隐藏语言确定*扩展*此文件。  
  
-   MasterPage.vstemplate  
  
     确定新的主控页和其依赖文件的内容，如果任何模板文件。  
  
## <a name="see-also"></a>另请参阅  
 [网站支持](../../extensibility/internals/web-site-support.md)