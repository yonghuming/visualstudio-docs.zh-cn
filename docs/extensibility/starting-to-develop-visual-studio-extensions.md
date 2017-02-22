---
title: "开始开发 Visual Studio 扩展 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "获取已启动和 Visual Studio 集成"
  - "Visual Studio 中集成"
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
caps.latest.revision: 29
caps.handback.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
---
# 开始开发 Visual Studio 扩展
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果您从未编写过 Visual Studio 扩展中的之前，您可能有一些问题。 我们列出了一些最常见的。 如果看不到您正在寻找的信息，使用的反馈按钮 \(**此页面是否有所帮助?** 屏幕底部\) 来询问您的想法。  
  
## 开发 Visual Studio 扩展需要哪些软件?  
 您需要安装 Visual Studio 2015 SDK 除了 Visual Studio 2015，以便开发 Visual Studio 扩展。   您可以作为常规安装的一部分安装 Visual Studio 2015 SDK 也可以将其安装更高版本上。 有关安装 Visual Studio SDK 的详细信息，请参阅 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## 使用 Visual Studio 扩展可以做何种操作?  
 天空是界限谈到设想不同 Visual Studio 扩展。 当然，大部分扩展会包含将做一些工作与编写代码，但是，不一定是这种情况。 下面是类型的扩展插件可以生成一些示例:  
  
-   对不包含在 Visual Studio 中，带有语法着色、 IntelliSense 和编译器和调试支持的语言的支持  
  
-   与其他模板、 代码重构，则新对话或工具窗口的扩展核心的工作效率工具 IDE 体验  
  
-   特定于域的类似数据的设计或云支持的方案的设计器  
  
 有关扩展的示例，请参阅 [Visual Studio 库](https://visualstudiogallery.msdn.microsoft.com/)。 您还可以看一看 [Visual Studio 打开源扩展](https://github.com/Microsoft/extendvs/blob/master/CommunityExtensions.md)。  
  
## 可以扩展的 Visual Studio 功能?  
 从理论上讲，您可以扩展几乎任何 Visual Studio 的一部分: 菜单、 工具栏、 命令、 windows、 解决方案、 项目、 编辑器和等等。  
  
 在实践中，我们发现大多数人想要扩展的功能是命令、 菜单和工具栏、 windows、 IntelliSense 和项目。 以下是相关的部分的链接:  
  
-   [扩展的菜单和命令](../extensibility/extending-menus-and-commands.md): 将您自己的项目添加到 Visual Studio 菜单和工具栏。 您可以使用它们启动 Visual Studio 的新功能或外部帮助应用程序。 您还可以为菜单项提供自定义快捷方式。  
  
-   [扩展和自定义工具窗口](../extensibility/extending-and-customizing-tool-windows.md): 扩展现有的工具窗口或创建您自己的工具窗口。 例如，可以添加到新的属性 **属性**, ，或者，可以创建一个新的工具窗口来添加附加功能。  
  
-   [编辑器和语言服务扩展](../extensibility/editor-and-language-service-extensions.md): 添加自己的自定义 Visual Studio 语言提供的 IntelliSense 或创建新的编程语言的支持。 您可以创建新的语句完成功能、 建议和新的快速信息工具提示。 使用电灯泡，您可以添加重构的建议和代码修复以支持新的编程语言。  
  
-   [扩展项目](../extensibility/extending-projects.md)  
  
-   [扩展的用户设置和选项](../extensibility/extending-user-settings-and-options.md)  
  
-   [扩展属性和属性窗口](../extensibility/extending-properties-and-the-property-window.md)  
  
-   [扩展 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)  
  
-   [Visual Studio 独立 Shell](../extensibility/visual-studio-isolated-shell.md)  
  
##  <a name="BKMK_ProjectTemplate"></a> 提供通过 VSSDK 有哪些项目模板?  
 两个主要类型的扩展是 Vspackage 和 MEF 扩展。 一般情况下，VSPackage 扩展使用的扩展的使用或扩展命令、 工具窗口和项目。 使用 MEF 扩展来扩展或自定义 Visual Studio 编辑器。  
  
 对于 Visual C\# 和 Visual Basic 扩展 VSSDK 提供了一个可以与创建菜单命令、 工具窗口和编辑器扩展的新项模板一起使用的空 VSIX 项目模板。 有关详细信息，请参阅[什么是 Visual Studio 2015 SDK 中的新增功能](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md)。 此外可以分发给其他用户使用此模板的包项目模板、 代码段和其他项目。  
  
 对于 c \+ \+，VSPackage 向导将提供用于添加菜单命令、 工具窗口和自定义编辑器的代码。  
  
 独立 Shell 模板用于包的版本可以在自己的品牌和分发与你自己的 Visual Studio shell 中的一个扩展。 以下主题演示了如何开始使用的扩展插件的每个类型:  
  
-   菜单命令: [使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   工具窗口: [使用一个工具窗口创建扩展](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   编辑器扩展: [在编辑器中的项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   基本 Vspackage: [使用 VSPackage 创建扩展](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
-   VSIX 项目模板: [Getting Started with VSIX 项目模板](../extensibility/getting-started-with-the-vsix-project-template.md)  
  
-   Visual Studio 独立 shell: [演练: 创建基本的独立的 Shell 应用程序](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
## 如何获取 my 扩展，如下所示 Visual Studio?  
 获得不错的提示设计为在扩展插件的 UI [Visual Studio 用户体验指南](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。  
  
## 在哪里可以找到 VSSDK 代码的示例?  
 每个在上一节中列出的链接具有分步演练演示了如何实现特定功能。 您还可以查找开源处的 GitHub 上的 VSSDK 示例 [Visual Studio 示例](https://aka.ms/vs2015sdksamples)。  
  
## 如何分发 my 扩展?  
 可以在另一台计算机上安装您的扩展，或将其作为通过双击安装.vsix 文件发送给您的朋友。 您可以了解有关在 VSIX 包的详细信息 [传送 Visual Studio 扩展](../extensibility/shipping-visual-studio-extensions.md)。  
  
 此外可以发布您在 Visual Studio 库，这使得对大量的 Visual Studio 客户可见的扩展。 针对库打包扩展的示例，请参阅 [演练: 发布 Visual Studio 扩展](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)。 有关需要执行的操作在库中发布的详细信息，请参阅 [的 Visual Studio 产品和扩展](https://visualstudiogallery.msdn.microsoft.com/)。