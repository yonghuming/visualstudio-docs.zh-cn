---
title: "Visual Studio SDK |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: 56
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 477f57bbca9c49e7d7d13155fc1f6e55ee4667a8
ms.openlocfilehash: efc5a2722757229057a91f5e3a6c2ad3681f5a89
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Visual Studio SDK 可帮助您扩展 Visual Studio 功能或集成到 Visual Studio 的新功能。 您可以分发您的扩展对其他用户，以及 Visual Studio 库。 以下是一些扩展 Visual Studio 的方式：  
  
-   向 IDE 添加命令、 按钮、 菜单和其他 UI 元素  
  
-   添加新功能的工具窗口  
  
-   扩展 IntelliSense 对于某种给定语言，或为新编程语言提供智能感知  
  
-   使用电灯泡提供提示和建议，帮助开发人员编写更好的代码  
  
-   启用对一种新语言的支持  
  
-   添加自定义项目类型  
  
-   让数百万开发人员通过 Visual Studio 库  
  
 如果您从未编写过 Visual Studio 扩展中的之前，您应发现和有关这些功能的详细信息[开始开发的 Visual Studio 扩展到](../extensibility/starting-to-develop-visual-studio-extensions.md)。  
  
## <a name="installing-the-visual-studio-sdk"></a>安装 Visual Studio SDK  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="whats-new-in-the-visual-studio-2015-sdk"></a>什么是 Visual Studio 2015 SDK 中的新增功能  
 Visual Studio SDK 具有一些新功能，包括电灯泡并允许您创建菜单命令、 工具窗口和编辑器扩展使用 VSIX 包的新项目项。 有关详细信息，请参阅[What's New in Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md)。  
  
## <a name="visual-studio-user-experience-guidelines"></a>Visual Studio 用户体验指南  
 获得不错的提示设计为在扩展插件的 UI [Visual Studio 用户体验指南](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。  
  
 您还可以了解如何让您外观精美具有高 DPI 设备上的扩展我们[寻址 DPI 问题](../extensibility/addressing-dpi-issues2.md)主题。  
  
 充分利用[映像服务和目录](../extensibility/image-service-and-catalog.md)最大的映像管理并支持高 DPI 和主题。  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>查找和安装现有的 Visual Studio 扩展  
 您可以找到 Visual Studio 扩展中的**扩展和更新**对话框中的，在**工具**菜单。 有关详细信息，请参阅[查找和使用 Visual Studio Extensions](../ide/finding-and-using-visual-studio-extensions.md)。 您还可以找到中的扩展[Visual Studio 库](https://visualstudiogallery.msdn.microsoft.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Visual Studio SDK 参考  
 您可以找到处的 Visual Studio SDK API 引用[Visual Studio SDK 引用](../extensibility/visual-studio-sdk-reference.md)。  
  
## <a name="visual-studio-sdk-samples"></a>Visual Studio SDK 示例  
 可以在 GitHub 上找到的 VS SDK 扩展的开放源代码示例[Visual Studio 示例](https://aka.ms/vs2015sdksamples)。 此 GitHub 存储库包含示例演示在 Visual Studio 中的各种可扩展功能。  
  
## <a name="other-visual-studio-sdk-resources"></a>其他 Visual Studio SDK 资源  
 如果有任何疑问 VSSDK 或者想要分享您开发扩展，则可以使用[Visual Studio Extensibility Forum](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)或[ExtendVS 分组聊天](https://gitter.im/Microsoft/extendvs)。  
  
 您可以找到详细信息中的[VSX Arcana 博客](http://blogs.msdn.com/b/vsx/)和一些由 Microsoft Mvp 撰写的博客︰  
  
-   [最喜欢的 Visual Studio 扩展](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Visual Studio 扩展性](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [扩展 Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>另请参阅  
 [使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [如何︰ 将可扩展性项目迁移到 Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)   
 [常见问题︰ 将加载项转换为 VSPackage 扩展](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [管理在托管代码中的多个线程](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [扩展的菜单和命令](../extensibility/extending-menus-and-commands.md)   
 [将命令添加到工具栏](../extensibility/adding-commands-to-toolbars.md)   
 [扩展和自定义工具窗口](../extensibility/extending-and-customizing-tool-windows.md)   
 [编辑器和语言服务扩展](../extensibility/editor-and-language-service-extensions.md)   
 [扩展项目](../extensibility/extending-projects.md)   
 [扩展的用户设置和选项](../extensibility/extending-user-settings-and-options.md)   
 [创建自定义项目和项模板](../extensibility/creating-custom-project-and-item-templates.md)   
 [扩展属性和属性窗口](../extensibility/extending-properties-and-the-property-window.md)   
 [扩展 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)   
 [使用并提供服务](../extensibility/using-and-providing-services.md)   
 [管理 Vspackage](../extensibility/managing-vspackages.md)   
 [Visual Studio 独立 Shell](../extensibility/visual-studio-isolated-shell.md)   
 [传送 Visual Studio 扩展](../extensibility/shipping-visual-studio-extensions.md)   
 [在 Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [对 Visual Studio SDK 的支持](../extensibility/support-for-the-visual-studio-sdk.md)   
 [存档](../extensibility/archive.md)   
 [Visual Studio SDK 参考](../extensibility/visual-studio-sdk-reference.md)
