---
title: "Visual Studio SDK |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: "56"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fbf9ab21b494bfc8b26251a8bdb79c16f81dc05d
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2017
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Visual Studio SDK 可帮助你扩展 Visual Studio 功能，或将新的功能集成到 Visual Studio。 你可以分发给其他用户，以及 Visual Studio Marketplace 你扩展。 以下是一些扩展 Visual Studio 的方式：  
  
-   将命令、 按钮、 菜单和其他 UI 元素添加到 IDE  
  
-   添加新功能的工具的窗口  
  
-   扩展 IntelliSense 对于给定语言，或对新编程语言提供 IntelliSense  
  
-   使用电灯泡提供提示和建议，帮助开发人员编写更好的代码  
  
-   启用对新语言的支持  
  
-   添加自定义项目类型  
  
-   访问数百万开发人员通过 Visual Studio 应用商店  
  
 如果您永远不会编写了之前的 Visual Studio 扩展，你应找到有关这些功能和的详细信息[开始开发 Visual Studio 扩展到](../extensibility/starting-to-develop-visual-studio-extensions.md)。  
  
## <a name="installing-the-visual-studio-sdk"></a>安装 Visual Studio SDK  
 Visual Studio SDK 是一项可选功能在 Visual Studio 安装。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>什么是 Visual Studio 2017 SDK 中的新增功能  
 Visual Studio SDK 具有一些新功能，如 VSIX v3 格式以及重大更改，这可能需要你更新你的扩展。 有关详细信息，请参阅[What's New in Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md)。  
  
## <a name="visual-studio-user-experience-guidelines"></a>Visual Studio 用户体验指南  
 获得很好的诀窍设计你的扩展中的 UI [Visual Studio 用户体验指南](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。  
  
 你还可以了解如何使你看上去漂亮高 DPI 使用在设备上的扩展我们[寻址 DPI 问题](../extensibility/addressing-dpi-issues2.md)主题。  
  
 利用[映像服务和目录](../extensibility/image-service-and-catalog.md)最大的映像管理以及对高 DPI 和主题支持。  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>查找并安装现有的 Visual Studio 扩展  
 你可以查找中的 Visual Studio 扩展**扩展和更新**对话框中的，在**工具**菜单。 有关详细信息，请参阅[查找和使用 Visual Studio 扩展](../ide/finding-and-using-visual-studio-extensions.md)。 你还可以查找中的扩展[Visual Studio Marketplace](https://marketplace.visualstudio.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Visual Studio SDK 参考  
 你可以找到在 Visual Studio SDK API 参考[Visual Studio SDK 参考](../extensibility/visual-studio-sdk-reference.md)。  
  
## <a name="visual-studio-sdk-samples"></a>Visual Studio SDK 示例  
 你可以在 GitHub 上找到的 VS SDK 扩展的开放源代码示例[Visual Studio 示例](https://aka.ms/vs2015sdksamples)。 此 GitHub 存储库包含说明 Visual Studio 中的各种可扩展功能的示例。  
  
## <a name="other-visual-studio-sdk-resources"></a>其他 Visual Studio SDK 资源  
 如果你有任何疑问 VSSDK 或想要共享您的经验开发扩展，则可以使用[Visual Studio 扩展性论坛](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)或[ExtendVS Gitter Chatroom](https://gitter.im/Microsoft/extendvs)。  
  
 你可以找到详细信息中的[VSX Arcana 博客](http://blogs.msdn.com/b/vsx/)和多个由 Microsoft Mvp 编写的博客：  
  
-   [收藏的 Visual Studio 扩展](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Visual Studio 扩展性](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [扩展 Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>另请参阅  
 [使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [如何： 将扩展性项目迁移到 Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)   
 [常见问题： 将外接程序转换为 VSPackage 扩展](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [管理在托管代码中的多个线程](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [扩展菜单和命令](../extensibility/extending-menus-and-commands.md)   
 [将命令添加到工具栏](../extensibility/adding-commands-to-toolbars.md)   
 [扩展和自定义工具窗口](../extensibility/extending-and-customizing-tool-windows.md)   
 [编辑器和语言服务扩展](../extensibility/editor-and-language-service-extensions.md)   
 [扩展项目](../extensibility/extending-projects.md)   
 [扩展的用户设置和选项](../extensibility/extending-user-settings-and-options.md)   
 [创建自定义项目和项模板](../extensibility/creating-custom-project-and-item-templates.md)   
 [扩展属性和属性窗口](../extensibility/extending-properties-and-the-property-window.md)   
 [扩展 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)   
 [使用和提供服务](../extensibility/using-and-providing-services.md)   
 [管理 Vspackage](../extensibility/managing-vspackages.md)   
 [Visual Studio 独立 Shell](../extensibility/visual-studio-isolated-shell.md)   
 [传送 Visual Studio 扩展](../extensibility/shipping-visual-studio-extensions.md)   
 [在 Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Visual Studio SDK 的支持](../extensibility/support-for-the-visual-studio-sdk.md)   
 [存档](../extensibility/archive.md)   
 [Visual Studio SDK 引用](../extensibility/visual-studio-sdk-reference.md)
