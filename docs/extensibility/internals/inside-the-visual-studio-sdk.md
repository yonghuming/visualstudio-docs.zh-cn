---
title: "在 Visual Studio SDK |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
caps.latest.revision: 30
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
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 565aaeb189ad129d5e4e26d9c73c080de2e77676
ms.lasthandoff: 04/05/2017

---
# <a name="inside-the-visual-studio-sdk"></a>在 Visual Studio SDK
本部分提供有关 Visual Studio 扩展，包括 Visual Studio 体系结构、 组件、 服务、 架构、 实用程序，以及类似的详细信息。  
  
## <a name="extensibility-architecture"></a>可扩展性体系结构  
 下图显示 Visual Studio 扩展性体系结构。 Vspackage 提供作为服务在 IDE 之间共享的应用程序功能。 标准 IDE 还提供了广泛的服务，如<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>，它提供的信息对 IDE 窗口化功能的访问。</xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 ![环境体系结构图](~/docs/extensibility/internals/media/environment.gif "environment")  
Visual Studio 体系结构的通用的视图  
  
## <a name="vspackages"></a>VSPackages  
 VSPackage 是软件模块，它们通过 UI 元素、服务、项目、编辑器和设计器来组成并扩展 Visual Studio。 Vspackage 是 Visual Studio 的中央体系结构单元。 有关详细信息，请参阅[Vspackage](../../extensibility/internals/vspackages.md)。  
  
## <a name="visual-studio-shell"></a>Visual Studio Shell  
 Visual Studio shell 提供基本功能，并支持其组件 Vspackage 和 MEF 扩展之间的跨通信。 有关详细信息，请参阅[Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md)。  
  
## <a name="user-experience-guidelines"></a>用户体验指南  
 如果你打算 for Visual Studio 中设计新的功能，你应看一看这些准则设计和可用性的提示︰ [Visual Studio 用户体验指南](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。  
  
## <a name="commands"></a>命令  
 命令是完成任务（如打印文档、刷新视图或创建新文件）的函数。  
  
 扩展 Visual Studio 时，你可以创建命令和使用 Visual Studio shell 它们进行注册。 你可以指定如何这些命令将显示在 IDE 中，例如，菜单或工具栏上。 自定义命令通常显示在**工具**菜单，然后显示一个工具窗口的命令将出现在**其他窗口**子菜单**视图**菜单。  
  
 在创建命令时，还必须为其创建事件处理程序。 事件处理程序确定命令何时可见或启用、 可让你修改其文本，以及保证，该命令合适方式进行响应时，它将激活。 在大多数情况下，IDE 处理命令通过使用<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口。</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Visual Studio 中的命令处理开头的最内层命令上下文中，基于本地选择，，到最外层的上下文，基于全局选择继续操作。 添加到主菜单的命令可立即用于脚本编写。  
  
 有关详细信息，请参阅[命令、 菜单和工具栏](../../extensibility/internals/commands-menus-and-toolbars.md)。  
  
## <a name="menus-and-toolbars"></a>菜单和工具栏  
 菜单和工具栏提供让用户来调用命令的方法。 菜单是行或列通常显示为单个文本工具窗口顶部的项的命令。 子菜单是当用户单击包含小箭头命令时，显示的辅助菜单。 用户右键单击某些用户界面元素时，会显示上下文菜单。 一些常见的菜单名包括**文件**，**编辑**，**视图**，和**窗口**。 有关详细信息，请参阅[扩展菜单和命令](../../extensibility/extending-menus-and-commands.md)。  
  
 工具栏是行或列的按钮和其他控件，如组合框、 列表框和文本框。 工具栏按钮通常具有图标图像，如的文件夹图标**打开的文件**命令或为打印机**打印**命令。 工具栏上的所有元素都都与命令关联。 单击工具栏按钮时，其关联的命令运行。 对于下拉列表控件，下拉列表中的每个项都与不同命令关联。 某些工具栏控件，如拆分器控件，均为混合。 控件的一端是工具栏按钮，另一端是在单击时其显示多个命令的向下箭头。  
  
## <a name="tool-windows"></a>工具窗口  
 工具窗口用于在 IDE 中显示信息。 **工具箱**，**解决方案资源管理器**，**属性**窗口中，和**Web 浏览器**是工具窗口的示例。  
  
 工具窗口通常提供用户可与之交互的各种控件。 例如，**属性**窗口使用户可以设置用于特定用途的对象的属性。 **属性**窗口是这个意义上来说，专用的但还常规，因为它可在许多不同的情况下。 同样，**输出**窗口专用化，因为它提供了基于文本的输出，但常规，因为 Visual Studio 中的许多子系统可以使用它来向 Visual Studio 用户提供输出。  
  
 请考虑下图的 Visual Studio 中，其中包含多个工具窗口。  
  
 ![屏幕截图](~/docs/extensibility/internals/media/t1gui.png "T1gui")  
  
 某些工具窗口一起停靠在单一的窗格显示解决方案资源管理器工具窗口和隐藏的其他工具窗口但使它们可通过单击选项卡。 图中显示了两个其他工具窗口，**错误列表**和**输出**窗口一起停靠在单一的窗格。  
  
 此外显示的是主文档窗格中，其中显示了多个编辑器窗口。 尽管工具窗口通常具有一个实例 (例如，你可以打开只有一个**解决方案资源管理器**)，编辑器窗口可以具有多个实例，其中每个用于编辑一个单独的文档，但所有这些停靠在同一窗格。 图中显示一个具有两个编辑器窗口，一个窗体设计器窗口，并显示启动页的浏览器窗口的文档窗格。 文档窗格中的所有窗口可通过单击选项卡上，但包含 EditorPane.cs 文件的编辑器窗口是可见的且活动。  
  
 扩展 Visual Studio 时，你可以创建 windows，以让 Visual Studio 用户交互的工具与您的扩展。 你还可以创建你自己让 Visual Studio 用户编辑文档的编辑器。 工具窗口和编辑器将集成到 Visual Studio 中，因为你没有进行编程以停靠或正确显示在选项卡上。 正确注册在 Visual Studio 中，它们将自动拥有工具窗口以及 Visual Studio 中的文档窗口的典型的功能。 有关详细信息，请参阅[扩展和自定义工具窗口](../../extensibility/extending-and-customizing-tool-windows.md)。  
  
## <a name="document-windows"></a>文档窗口  
 文档窗口是框架的子窗口的多文档界面 (MDI) 窗口。 文档窗口通常用于承载文本编辑器、 窗体编辑器 （也称为设计器） 或编辑控件，但它们也可以承载其他功能的类型。 **新文件**对话框包括 Visual Studio 提供的文档窗口的示例。  
  
 大多数编辑器的特定于编程语言或文件类型，如 HTML 页面、 框架集、 c + + 文件或标头文件。 通过选择中的模板**新文件**对话框中，用户动态创建一个文档窗口是与模板关联的文件类型的编辑器。 当用户打开现有文件，也将创建一个文档窗口。  
  
 文档窗口被限制为 MDI 工作区。 每个文档窗口在顶部，有一个选项卡和 tab 键顺序链接到可能的 MDI 区域中打开其他窗口。 右键单击文档窗口的选项卡显示包括选项以将 MDI 区域拆分为多个水平或垂直选项卡组的快捷菜单。 拆分 MDI 区使同时查看多个文件。 有关详细信息，请参阅[文档窗口](../../extensibility/internals/document-windows.md)。  
  
## <a name="editors"></a>编辑器  
 Visual Studio 编辑器，可自定义它并将它用于自己的内容的类型通过 Managed Extensibility Framework (MEF) 中。 在许多情况下不需要创建 VSPackage 来扩展编辑器，尽管你想要包括从 shell （例如，菜单命令或快捷键） 的功能，则你可以组合使用 VSPackage 的 MEF 扩展。  
  
 你还可以创建自定义编辑器，例如，如果你想要读取和写入到数据库，或者如果你想要使用设计器。 你还可以使用如记事本或 Microsoft 写字板外部编辑器。 有关详细信息，请参阅[编辑器和语言服务扩展](../../extensibility/editor-and-language-service-extensions.md)。  
  
## <a name="language-services"></a>语言服务  
 如果您希望 Visual Studio 编辑器以支持新的编程关键字或甚至新的编程语言，则创建语言服务。 每个语言服务可实现某些编辑器功能，完全、 部分，或根本不容易。 根据配置方式，该语言服务可以提供语法突出显示、 大括号匹配、 IntelliSense 支持和在编辑器中的其他功能。  
  
 语言服务的核心是一个分析器和扫描程序。 扫描程序 （或词法分析器） 将源文件划分为称为令牌的元素，并一个分析器建立这些令牌之间的关系。 当你创建语言服务时，则必须实现分析器和扫描程序，以便 Visual Studio 可以了解的令牌和语言语法。 你可以创建托管或非托管语言服务。 有关详细信息，请参阅[旧语言服务可扩展性](../../extensibility/internals/legacy-language-service-extensibility.md)。  
  
## <a name="projects"></a>项目  
 在 Visual Studio 中，项目是开发人员用于组织和生成的源代码和其他资源的容器。 项目的让组织、 生成、 调试和部署源代码、 对 Web 服务和数据库，以及其他资源的引用。 Vspackage 可以通过提供项目类型、 项目子类型和自定义工具来扩展 Visual Studio 项目系统。  
  
 项目还可能收集到一个解决方案，这是协同工作以创建应用程序的一个或多个项目中的分组。 与解决方案的项目和状态信息存储在两个解决方案文件、 基于文本的解决方案 (.sln) 文件和二进制解决方案用户选项 (.suo) 文件。 这些文件是类似于在的早期版本中使用的组 (文件.vbg) 文件[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]，和工作区 (.dsw) 和用户选项 (.opt) 文件的早期版本中使用[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]。  
  
 有关详细信息，请参阅[项目](../../extensibility/internals/projects.md)和[解决方案](../../extensibility/internals/solutions.md)。  
  
## <a name="project-and-item-templates"></a>项目和项模板  
 Visual Studio 包含预定义的项目模板和项目项模板。 你可以还使你自己的模板或获取在社区中的模板，然后将其集成到 Visual Studio。 [MSDN 代码库](http://code.msdn.microsoft.com/Project/ProjectDirectory.aspx?ProjectSearchText=visual%20studio)是转模板和扩展的位置。  
  
 模板包含的项目结构和生成特定种类的应用程序、 控件、 库或类所需的基本文件。 如果你想要开发软件类似于其中一个模板，创建基于模板的项目，，然后修改该项目中的文件。  
  
> [!NOTE]
>  此模板体系结构不支持[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]项目。 有关如何创建[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]项目模板，请参阅[设计向导](/cpp/ide/designing-a-wizard)。  
  
 有关详细信息，请参阅[添加项目和项目项模板](../../extensibility/internals/adding-project-and-project-item-templates.md)。  
  
## <a name="properties-and-options"></a>属性和选项  
 **属性**窗口将显示一个或多个选定的项的属性︰[扩展属性](../../extensibility/internals/extending-properties.md)选项页包含一系列的选项适用于特定组件，例如一种编程语言或 VSPackage:[选项和选项页](../../extensibility/internals/options-and-options-pages.md)。 设置是通常与 UI 相关的功能，可以导入和导出︰[对用户设置的支持](../../extensibility/internals/support-for-user-settings.md)。  
  
## <a name="visual-studio-services"></a>Visual Studio 服务  
 服务提供一组特定的组件使用的接口。 Visual Studio 提供了一组可由任何组件，包括扩展的服务。 例如，Visual Studio 服务使工具窗口，以显示或隐藏动态，启用对帮助、 状态栏或 UI 事件的访问。 Visual Studio 编辑器还可以导入的编辑器扩展的服务提供。 有关详细信息，请参阅[使用和提供服务](../../extensibility/using-and-providing-services.md)。  
  
## <a name="debugger"></a>调试器  
 调试器是特定于语言的调试组件的用户界面。 如果你已创建新的语言服务，你将需要创建特定的调试引擎将在挂接到调试器。 有关详细信息，请参阅[Visual Studio 调试器扩展性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)。  
  
## <a name="source-control"></a>源代码管理  
 有关实现源代码管理插件或 VSPackage 的信息，请参阅[源代码管理](../../extensibility/internals/source-control.md)。  
  
## <a name="wizards"></a>向导  
 你也可以使用新的项目类型创建结合使用的向导，在创建该类型的新项目时，你的用户，以便该向导可以帮助进行正确的决策。 有关详细信息，请参阅[向导](../../extensibility/internals/wizards.md)。  
  
## <a name="custom-tools"></a>自定义工具  
 自定义工具，你将工具与项目中的项相关联和运行该工具，每当保存该文件。 有关详细信息，请参阅[自定义工具](../../extensibility/internals/custom-tools.md)。  
  
## <a name="vssdk-utilities"></a>VSSDK 实用程序  
 VSSDK 包括一套实用程序可能需要若要使用的 Vspackage 的不同方面。 有关详细信息，请参阅[VSSDK 实用工具](../../extensibility/internals/vssdk-utilities.md)。  
  
## <a name="using-windows-installer"></a>使用 Windows 安装程序  
 在某些情况下，可能需要使用 Windows Installer，而不是 VSIX 安装程序︰ 例如，你可能需要向注册表写入。 有关使用你的扩展支持 Windows 安装程序的信息，请参阅[与 Windows Installer 安装 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)。  
  
## <a name="help-viewer"></a>帮助查看器  
 你可以将你自己的帮助和 F1 页集成到帮助查看器。 有关详细信息，请参阅[Microsoft 帮助查看器 SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md)。
