---
title: "支持的网站模板 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "我们网站项目中，模板"
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 支持的网站模板
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 网站项目模板和项模板提供了可重用，并且加速的自定义项的网站项目和项存根将取消开发过程的需要从头开始创建新网站项目和项目。  有关 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 模板的更多信息，请参见 [创建自定义项目和项模板](../../ide/creating-project-and-item-templates.md)。  
  
## 项模板文件夹  
 Web 项目模板模板位于 \[\]*Visual Studio 安装路径*\\Common7\\IDE\\ProjectTemplates\\Web \\，通常安装的每个都与 web 编程语言命名的子文件夹。  
  
## 项目文件  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 集成 \(IDE\)开发环境 \(ide\) 需要一个项目文件扩展名作为一种映射模板到正确的项类型。  由于 Web 项目没有一个项目文件，虚假的项目文件扩展名 .webproj 注册支持此操作。  
  
 或者，语言名称可以将字符串添加到模板使 Web 项目系统将 **添加新项目** 对话框的语言默认名称基于模板的项目。  该字符串必须是文件的第一行，并且必须与该名称注册在 Intellisense 引擎注册的 AddItemLanguageName 下和名称签入项的子类型 \(\) 下。 VsTemplate  有关更多信息，请参见 [网站支持属性](../../extensibility/internals/web-site-support-attributes.md)。  
  
 如果该字符串不存在，则 Web 项目系统将尝试确定根据语言特性的默认语言，页的文件扩展名添加到由 Web 项目模板模板项目。  
  
## 项目模板  
 网站项目模板用于生成新的 web 响应 **文件** 菜单的 **新网站** 命令。  三个网站项目类型是当前支持:  
  
-   空网站项目  
  
-   网站项目  
  
-   web services 项目  
  
### 空网站项目  
 这些文件创建一个新的空网站以响应 **空网站** 命令，这些点以后可用于在 **文件** 菜单的 **新网站** :  
  
-   EmptyWeb.vstemplate  
  
     引导新的空网站创建的模板文件。  
  
-   EmptyWeb.webproj  
  
     此文件是项目模板系统的项目。  它在 EmptyWeb.vstemplate 文件满足项目文件引用。  
  
### 网站项目  
 这些文件创建新网站以响应 **ASP.NET 网站** 命令，这些点以后可用于在 **文件** 菜单的 **新网站** :  
  
-   Default.aspx  
  
     新网站的系统设计的主页。  语言特性指定 codebehind 语言，因此， CodeFile 属性指定包含 codebehind 代码的依赖文件与此页。  
  
-   Default.aspx.*扩展*  
  
     包含系统设计的主页的 codebehind 代码的依赖文件。  codebehind 语言确定此文件 *扩展* 。  
  
-   web.config  
  
     根 web.site 配置文件。  
  
-   WebApplication.vstemplate  
  
     确定网站解决方案目录并强制 App\_Data 文件夹中创建的模板文件。  
  
-   WebApplication.webproj  
  
     此文件是项目模板系统的项目。  它在 WebApplication.vstemplate 文件满足项目文件引用。  
  
### web services 项目  
 这些文件创建新网站响应点以后可用于在 **文件** 菜单的 **新网站** 的 **ASP.NET web 服务** 命令:  
  
-   Service.asmx  
  
     新的 web 服务的 HTML 页。  语言特性指定 codebehind 语言，因此， CodeBehind 特性指定包含 codebehind 代码的依赖文件与此服务。  
  
-   服务。 *扩展*  
  
     实现服务类的依赖文件。  codebehind 语言确定此文件 *扩展* 。  
  
-   web.config  
  
-   根 web.site 配置文件。  
  
-   WebService.vstemplate  
  
     确定网站解决方案目录并强制 App\_Data 和 App\_Code 文件夹中创建的模板文件。  服务。*扩展* 文件复制到 App\_Code 文件夹中。  
  
-   WebService.webproj  
  
     此文件是项目模板系统的项目。  它在 WebService.vstemplate 文件满足项目文件引用。  
  
## 项目项模板文件夹  
 Web 项目项模板模板位于 \[\]*Visual Studio 安装路径*\\Common7\\IDE\\ItemTemplates\\Web \\，通常安装的每个都有其 web 编程语言命名的子文件夹。  
  
## 项目项模板  
 网站项目项模板用于将新网页添加到网站以响应 **添加现有项目** 命令。  这些网页当前支持:  
  
-   新类  
  
-   新的 HTML 页  
  
-   新的 Web 窗体  
  
-   新的母版页  
  
### 新类  
 此模板创建定义空的类以响应 **添加新类** 命令的一个新的源文件。  
  
-   类。 *扩展*  
  
     实现空的类的源文件。  codebehind 语言确定此文件 *扩展* 。  
  
-   Class.vstemplate  
  
     创建源文件并确定其内容的模板文件。  
  
### 新的 HTML 页  
 此模板创建新网页响应 **添加新的 HTML 页** 命令。  
  
-   HTMLPage.htm  
  
     网页的起始内容。  此网页通常没有关联的 codebehind 依赖文件。  用一个关联的 codebehind 文件创建智能页，请使用 Web 窗体模板。  
  
-   HTMLPage.vstemplate  
  
     创建网页并确定其内容的模板文件。  
  
### 新 WebForm  
 此模板创建新的智能网页响应 **添加新 Web 窗体** 命令。  
  
 创建相关的 codebehind 源文件，请选择 **将代码置于单独的文件**。  否则没有空脚本块和 AMP\_LT% 页 %AMP\_GT 指令挂钩依赖文件的一个网页创建。  
  
 若要创建选定的母版页的内容页上，选择 **选择母版页**。  
  
-   WebForm.aspx  
  
     网页的起始内容。  此网页没有关联的 codebehind 依赖文件。  
  
-   WebForm\_cb.aspx  
  
     网页的起始内容。  此网页具有关联的 codebehind 依赖文件。  
  
-   Codebehind。 *扩展*  
  
     实现 webform 类的依赖文件。  codebehind 语言确定此文件 *扩展* 。  
  
-   ContentPage.aspx  
  
     网页的起始内容作为内容页。  此网页没有关联的 codebehind 依赖文件。  
  
-   ContentPage\_cb.aspx  
  
     网页的起始内容作为内容页。  此网页具有关联的 codebehind 依赖文件。  
  
-   WebForm.vstemplate  
  
     确定新网页及其依赖文件的内容的模板文件，因此，如果有的话\)。  
  
### 新的母版页  
 此模板创建新的母版页响应 **添加新的母版页** 命令。  
  
 创建相关的 codebehind 源文件，请选择 **将代码置于单独的文件**。  否则没有空脚本块和 AMP\_LT% 页 %AMP\_GT 指令挂钩依赖文件的一个网页创建。  
  
-   MasterPage.master  
  
     母版页的起始内容。  此母版页没有关联的 codebehind 依赖文件。  
  
-   MasterPage\_cb.master  
  
     母版页的起始内容。  此母版页具有关联的 codebehind 依赖文件。  
  
-   Codebehind。*扩展*  
  
     实现母版页类的依赖文件。  codebehind 语言确定此文件 *扩展* 。  
  
-   MasterPage.vstemplate  
  
     确定新母版页及其依赖文件的内容的模板文件，因此，如果有的话\)。  
  
## 请参阅  
 [网站支持](../../extensibility/internals/web-site-support.md)