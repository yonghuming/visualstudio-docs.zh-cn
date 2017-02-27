---
title: "在 Visual Studio SDK | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "路线图，Visual Studio 集成 SDK"
  - "Visual Studio 集成 SDK 蓝图"
  - "集成路线图，Visual Studio SDK"
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
caps.latest.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 30
---
# 在 Visual Studio SDK
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

本部分提供有关 Visual Studio 扩展，包括 Visual Studio 体系结构、 组件、 服务、 架构、 实用程序和类似的内容的详细信息。  
  
## 扩展性体系结构  
 下图显示 Visual Studio 扩展性体系结构。 VSPackages 提供作为服务在 IDE 之间共享的应用程序功能。 对标准 IDE 还提供了广泛的服务，如 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, ，它们提供对 IDE 窗口功能的访问。  
  
 ![环境体系结构图](../../extensibility/internals/media/environment.png "environment")  
Visual Studio 体系结构的通用的视图  
  
## Vspackage  
 Vspackage 是一些软件模块，它们构成，并且使用用户界面元素、 服务、 项目、 编辑器和设计器来扩展 Visual Studio。 Vspackage 是 Visual Studio 的中央体系结构单元。 有关更多信息，请参见[Vspackage](../../extensibility/internals/vspackages.md)。  
  
## Visual Studio Shell  
 Visual Studio shell 提供基本功能和支持其组件 Vspackage 和 MEF 扩展之间的跨通信。 有关详细信息，请参阅[Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md)。  
  
## 用户体验指南  
 如果您打算设计的 Visual Studio 的新功能，您应该看一看以下准则，以便设计和可用性的提示: [Visual Studio 用户体验指南](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。  
  
## 命令  
 命令是完成任务，如打印文档、 刷新视图，或创建一个新的文件的函数。  
  
 扩展 Visual Studio 时，可以创建命令并将它们注册 Visual Studio shell。 您可以指定如何这些命令将显示在 IDE 中，例如，菜单或工具栏上。 自定义命令通常出现在 **工具** 菜单上和用于显示工具窗口的命令将显示在 **其他窗口** 的子菜单 **视图** 菜单。  
  
 当您创建一个命令时，还必须为其创建事件处理程序。 事件处理程序确定命令何时是可见的还是已启用，让你能够修改其文本，并保证，该命令会做出适当响应激活时。 在大多数情况下，IDE 处理命令通过使用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 接口。 Visual Studio 中的命令的处理开头的最内层命令上下文，基于本地的选择，并且继续到最外层的上下文，基于全局的选择。 立即提供用于脚本编写了一些命令添加到主菜单。  
  
 有关详细信息，请参阅[命令、 菜单和工具栏](../../extensibility/internals/commands-menus-and-toolbars.md)。  
  
## 菜单和工具栏  
 菜单和工具栏提供让用户调用命令的方法。 菜单为行或列通常显示为工具窗口顶部的单个文本项的命令。 子菜单是辅助显示当用户单击包含一个小箭头的命令的菜单。 当用户右键单击某些用户界面元素时出现上下文相关菜单。 某些常见的菜单名称不 **文件**, ，**编辑**, ，**视图**, ，和 **窗口**。 有关详细信息，请参阅[扩展的菜单和命令](../../extensibility/extending-menus-and-commands.md)。  
  
 工具栏是行或列的按钮和其他控件，如组合框、 列表框和文本框。 工具栏按钮通常具有图标图像，如的文件夹图标 **打开的文件** 命令或为打印机 **打印** 命令。 工具栏上的所有元素都均与命令关联。 当您单击工具栏按钮时，其关联的命令运行。 对于下拉列表控件，下拉列表中的每个项都使用不同的命令相关联。 某些工具栏控件，如拆分器控件均混合。 该控件的一侧是一个工具栏按钮，另一方面是显示多个命令，单击时其向下箭头。  
  
## 工具窗口  
 工具窗口用于在 IDE 中显示的信息。**工具箱**, ，**解决方案资源管理器**, ，**属性** 窗口中，和 **Web 浏览器** 是工具窗口的示例。  
  
 工具窗口通常会提供用户可与之交互的各种控件。 例如， **属性** 窗口让用户设置对象的具有特定用途的属性。**属性** 窗口是这个意义上讲，专用的但还常规，因为它可以采用许多不同的情况。 同样， **输出** 窗口是否专用化，因为它提供了基于文本的输出，但常规，因为在 Visual Studio 中的多个子系统可以使用它来向 Visual Studio 用户提供输出。  
  
 请考虑下面的 Visual Studio 中，其中包含多个工具窗口的图片。  
  
 ![屏幕快照](../../extensibility/internals/media/t1gui.png "T1gui")  
  
 某些工具窗口一起停靠在一个窗格是显示解决方案资源管理器工具窗口和其他工具窗口将隐藏但使它们可通过单击选项卡。 图中显示了两个其他工具窗口， **错误列表** 和 **输出** 窗口中上一个窗格, 停靠在一起。  
  
 此外显示的是主文档窗格，其中显示多个编辑器窗口。 尽管工具窗口通常具有一个实例 \(例如，您可以打开只有一个 **解决方案资源管理器**\)，编辑器窗口可以具有多个实例，其中每个将用来编辑一个单独的文档，但所有这些停靠在同一窗格中。 图中显示一个具有两个编辑器窗口，一个窗体设计器窗口中，并显示启动页的浏览器窗口的文档窗格。 在文档窗格中的所有窗口都都可通过单击选项卡上，但编辑器窗口包含 EditorPane.cs 文件可见并处于活动状态。  
  
 扩展 Visual Studio 时，您可以创建允许 Visual Studio 用户的 windows 进行交互的工具与您的扩展。 此外可以创建您自己编辑器，以允许编辑文档的 Visual Studio 用户。 工具窗口和编辑器将集成到 Visual Studio 中，因为您没有进行编程以停靠或选项卡上正确显示。 当正确注册在 Visual Studio 中时，它们将自动具有工具窗口与 Visual Studio 中的文档窗口的典型功能。 有关详细信息，请参阅[扩展和自定义工具窗口](../../extensibility/extending-and-customizing-tool-windows.md)。  
  
## 文档窗口  
 文档窗口是一个多文档界面 \(MDI\) 窗口的组帧的子窗口。 文档窗口通常用于宿主的文本编辑器、 窗体编辑器 \(也称为设计器\) 或编辑控件，但它们也可以承载其他功能的类型。**新文件** 对话框中包括 Visual Studio 提供的文档窗口中的示例。  
  
 大多数编辑器都是特定于编程语言或文件类型，如 HTML 页面、 框架集、 c \+ \+ 文件或标头文件。 通过选择中的模板 **新文件** 对话框中，用户动态创建的文档窗口是与模板关联的文件类型的编辑器。 用户打开一个现有文件时，还会创建一个文档窗口。  
  
 文档窗口被限制为 MDI 工作区。 每个文档窗口顶部，在具有一个选项卡和 tab 键顺序链接至其他 MDI 方面可能打开的窗口。 右键单击文档窗口的选项卡会显示快捷菜单，其中包含要将 MDI 区域拆分为多个水平或垂直选项卡组选项。 拆分 MDI 区使多个文件，您可以在同一时间。 有关更多信息，请参见[文档窗口](../../extensibility/internals/document-windows.md)。  
  
## 编辑器  
 Visual Studio 编辑器允许您自定义它并将它用于您自己的内容的类型通过 Managed Extensibility Framework \(MEF\)。 在许多情况下不需要创建 VSPackage 扩展编辑器中，但如果您想要包括从命令行界面 \(例如，菜单命令或快捷键\) 的功能，您可以将与 VSPackage MEF 扩展。  
  
 此外可以创建自定义编辑器中的，例如，如果您想要读取和写入到数据库，或如果您想要使用设计器。 此外可以使用如记事本或 Microsoft 写字板外部编辑器。 有关更多信息，请参见[编辑器和语言服务扩展](../../extensibility/editor-and-language-service-extensions.md)。  
  
## 语言服务  
 如果您希望 Visual Studio 编辑器以支持新的编程关键字或甚至新编程语言，您将创建语言服务。 完全、 部分，或根本不是，每个语言服务可能实现某些编辑器功能。 根据配置方式，语言服务可以提供语法突出显示、 大括号匹配、 IntelliSense 支持和编辑器中的其他功能。  
  
 语言服务的核心是一个分析器和扫描程序。 扫描仪 \(或词法分析器\) 将源文件分割成称为标记的元素，并分析程序建立这些令牌之间的关系。 当创建语言服务时，必须实现分析器和扫描程序，以便 Visual Studio 可以理解的标记和语言的语法。 您可以创建托管或非托管语言服务。 有关详细信息，请参阅[遗留语言服务可扩展性](../../extensibility/internals/legacy-language-service-extensibility.md)。  
  
## 项目  
 在 Visual Studio 中，项目是开发人员用于组织和构建的源代码和其他资源的容器。 项目的让组织、 生成、 调试和部署的源代码，请对 Web 服务和数据库，以及其他资源的引用。 Vspackage 可以扩展 Visual Studio 项目系统提供的项目类型和项目的子类型，并自定义工具。  
  
 项目可能也不会收集到一个解决方案是协同工作以创建应用程序的一个或多个项目的分组。 适用于解决方案的项目和状态信息存储在两个解决方案文件、 基于文本的解决方案 \(.sln\) 文件和二进制解决方案用户选项 \(.suo\) 文件。 这些文件是相似的早期版本中使用的组 \(文件.vbg\) 文件 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], ，并在工作区 \(.dsw\) 和用户选项 \(.opt\) 文件中使用早期版本的 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)]。  
  
 有关详细信息，请参阅[项目](../../extensibility/internals/projects.md)和[解决方案](../../extensibility/internals/solutions.md)。  
  
## 项目和项模板  
 Visual Studio 包含预定义的项目模板和项目项模板。 您可以还使您自己的模板或获取从社区的模板，然后将它们集成到 Visual Studio。[MSDN 代码库](http://code.msdn.microsoft.com/Project/ProjectDirectory.aspx?ProjectSearchText=visual%20studio) 是寻求模板和扩展的位置。  
  
 模板包含的项目结构和生成特定类型的应用程序、 控件、 库或类所需的基本文件。 当您想要开发软件类似于一个模板时，创建基于模板的项目，然后修改该项目中的文件。  
  
> [!NOTE]
>  不支持此模板体系结构 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 项目。 有关如何创建 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 项目模板，请参阅 [设计向导](/visual-cpp/ide/designing-a-wizard)。  
  
 有关更多信息，请参见[添加项目和项目项模板](../../extensibility/internals/adding-project-and-project-item-templates.md)。  
  
## 属性和选项  
 **属性** 窗口将显示一个或多个选定的项的属性: [将属性扩展](../../extensibility/internals/extending-properties.md) 选项页包含一系列的选项适用于特定组件，例如一种编程语言或 VSPackage: [选项和选项页](../../extensibility/internals/options-and-options-pages.md)。 设置是通常与 UI 相关的功能，可以导入和导出: [用户设置的的支持](../../extensibility/internals/support-for-user-settings.md)。  
  
## Visual Studio 服务  
 一种服务提供了一组特定的组件使用的接口。 Visual Studio 提供了一组可由任何组件，包括扩展的服务。 例如，Visual Studio 服务使工具窗口，以显示或隐藏动态，启用访问帮助、 状态栏、 或 UI 事件。 Visual Studio 编辑器还提供可通过编辑器扩展导入的服务。 有关详细信息，请参阅[使用并提供服务](../../extensibility/using-and-providing-services.md)。  
  
## 调试器  
 调试器是特定于语言的调试组件的用户界面。 如果创建新的语言服务后，您将需要创建到调试器挂接到一个特定的调试引擎。 有关详细信息，请参阅[Visual Studio 调试器可扩展性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)。  
  
## 源代码管理  
 有关实现的源代码管理插件或 VSPackage 的信息，请参阅 [源代码管理](../../extensibility/internals/source-control.md)。  
  
## 向导  
 您也可以使用新的项目类型创建结合使用的向导，在创建该类型的新项目时，您的用户，以便向导可以帮助做出正确的决策。 有关详细信息，请参阅[向导](../../extensibility/internals/wizards.md)。  
  
## 自定义工具  
 自定义工具，可以将一种工具与项目中的项相关联并保存该文件时运行该工具。 有关更多信息，请参见[自定义工具](../../extensibility/internals/custom-tools.md)。  
  
## VSSDK 实用程序  
 VSSDK 包括一组可能需要为了使用 Vspackage 的不同方面的实用程序。 有关详细信息，请参阅[VSSDK 实用程序](../../extensibility/internals/vssdk-utilities.md)。  
  
## 使用 Windows 安装程序  
 在某些情况下，可能需要使用 Windows 安装程序，而不是 VSIX 安装程序: 例如，您可能需要向注册表写入。 有关使用您的扩展支持 Windows 安装程序的信息，请参阅 [使用 Windows Installer 安装 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)。  
  
## 帮助查看器  
 您可以将您自己的帮助和 F1 页集成到帮助查看器。 有关更多信息，请参见[Microsoft 帮助查看器 SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md)。