---
title: "设计 XML 命令表 (。Vsct) 文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ca277abe07ffe843ed3f4106615796340f5367a4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="designing-xml-command-table-vsct-files"></a>设计 XML 命令表 (。Vsct) 文件
XML 命令表 (.vsct) 文件描述的布局和命令项的对为 VSPackage 的外观。 命令项包括按钮、 组合框、 菜单、 工具栏和命令项组。 本主题介绍 XML 命令表文件、 它们如何影响命令项目和菜单，以及如何创建它们。  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>命令、 菜单、 组和.vsct 文件  
 .vsct 文件会组织围绕命令、 菜单和命令组。 .Vsct 文件中的 XML 标记表示每个这些项，以及其他关联的项，如命令按钮、 命令放置和位图。  
  
 当你通过运行创建新的 VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]包模板，该模板会生成具有所需的元素为菜单命令、 工具窗口中或自定义编辑器中的，具体取决于你选择的.vsct 文件。 然后可以修改此.vsct 文件，以满足特定的 VSPackage 的要求。 有关如何修改.vsct 文件的示例，请参阅中的示例[扩展菜单和命令](../../extensibility/extending-menus-and-commands.md)。  
  
 若要创建新的空白.vsct 文件，请参阅[如何： 创建。Vsct 文件](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)。 创建后，你将添加 XML 元素、 属性和值到文件来描述命令项布局。 有关详细的 XML 架构，请参阅[VSCT XML 架构参考](../../extensibility/vsct-xml-schema-reference.md)。  
  
## <a name="differences-between-ctc-and-vsct-files"></a>.Ctc 和.vsct 文件之间的差异  
 虽然.vsct 文件中的 XML 标记背后的含义是相同的为中现在已弃用.ctc 文件格式，其实现是稍有不同。  
  
-   新 **\<extern >**标记是，引用要编译，例如，那些用于其他.h 文件[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]工具栏。  
  
-   而.vsct 文件支持**/ 包括**语句，.ctc 文件一样，它还提供了一个新\<**导入 >**元素。 差异在于， **/ 包括**加入**所有**的信息，但\<**导入 >**加入只有名称的名称。  
  
-   虽然.ctc 文件需要在其中定义预处理器指令的标头文件，不需要的.vsct 文件。 相反，将你的指令放置在符号表中，位于**\<符号 >**元素，位于.vsct 文件的底部。  
  
-   .vsct 文件功能**\<批注 >**标记，该对话框可以嵌入您喜欢，如说明或甚至图片的任何信息。  
  
-   值作为上项的属性存储。  
  
-   可以单独存储或堆积命令标志。  Intellisense，但是，不在无效堆积的命令标志。 有关命令标志的详细信息，请参阅[命令标志元素](../../extensibility/command-flag-element.md)。  
  
-   你可以指定多个类型，例如拆分下拉菜单、 组合，等等。  
  
-   Guid 不验证。  
  
-   每个 UI 元素都有一个字符串，表示与其显示的文本。  
  
-   父是可选的。 如果省略，则使用"组未知"的值。  
  
-   该图标参数是可选的。  
  
-   将文件位图部分-.ctc 相同，只不过你现在可以指定文件名称通过将由 vsct.exe 编译器请求在编译时的 href。  
  
-   ResID-旧位图资源 ID 可以使用，并且仍如下所示.ctc 文件的操作方式相同。  
  
-   HRef-一个新的方法，以便您可以指定位图资源的文件名称。 它假设将使用所有，因此可以省略使用的部分。 编译器将首先搜索本地资源的文件，然后在任何网络共享，并定义 /I 开关的任何资源。  
  
-   键绑定-不再需要指定一个仿真程序。 如果指定一个，则编译器将假定编辑器和仿真程序是相同。  
  
-   Keychord-已删除。 新的格式为 Key1、 Mod1、 Key2、 Mod2。  你可以指定字符、 十六进制、 或 VK 常量。  
  
 新的编译器、 vsct.exe，编译.ctc 和.vsct 文件。 旧的 ctc.exe 编译器，但是，将不识别也不编译.vsct 文件。  
  
 Vsct.exe 编译器可用于将现有.cto 文件转换为一个.vsct 文件。 有关此的详细信息，请参阅[如何： 创建。从现有的 Vsct 文件。首席技术官文件](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file)。  
  
## <a name="the-vsct-file-elements"></a>.Vsct 文件元素  
 命令表具有以下层次结构和元素：  
  
 [CommandTable 元素](../../extensibility/commandtable-element.md)-表示的所有命令、 菜单组和 VSPackage 与关联的菜单。  
  
 [Extern 元素](../../extensibility/extern-element.md)— 引用你想要与.vsct 文件合并任何外部.h 文件。  
  
 [包括元素](../../extensibility/include-element.md)— 引用你想要编译 your.vsct 文件以及任何其他标头 (.h) 文件。 .Vsct 文件可以包含.h 文件包含定义 IDE 或另一个 VSPackage 提供的命令、 菜单组和菜单的常量。  
  
 [命令元素](../../extensibility/commands-element.md)-表示所有可执行的单个命令。 每个命令具有以下四个子元素：  
  
 [菜单元素](../../extensibility/menus-element.md)-表示的菜单和工具栏在 VSPackage 中的所有。 菜单是组的命令的容器。  
  
 [Groups 元素](../../extensibility/groups-element.md)-表示所有在 VSPackage 中的组。 组是各条命令组成的集合。  
  
 [按钮元素](../../extensibility/buttons-element.md)-表示所有的命令按钮和在 VSPackage 中的菜单项。 按钮，可以与命令相关联的可视控件。  
  
 [位图元素](../../extensibility/bitmaps-element.md)-表示所有按钮在 VSPackage 中的所有位图。 位图为显示下一步或上的命令按钮，具体取决于上下文的图片。  
  
 [CommandPlacements 元素](../../extensibility/commandplacements-element.md)-指示单个命令其中应被放置在你的 VSPackage 的菜单中的其他位置。  
  
 [VisibilityConstraints 元素](../../extensibility/visibilityconstraints-element.md)-指定是否命令显示在所有时间，或仅在某些上下文中，例如显示特定的对话框或窗口时。 仅当指定的上下文处于活动状态时，将显示菜单和命令，并提供此元素的值。 默认行为是在所有时间显示的命令。  
  
 [键绑定元素](../../extensibility/keybindings-element.md)-指定任何键绑定的所有命令。 也就是说，一个或多个键组合必须按下执行命令，如**CTRL + S**。  
  
 [UsedCommands 元素](../../extensibility/usedcommands-element.md)-通知[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]虽然当前 VSPackage 处于活动状态时，将由其他代码中，实现指定的命令，它提供的命令实现的环境。  
  
 `Symbols Element`-包含符号名称和所有包中命令的 GUID Id。  
  
## <a name="vsct-file-design-guidelines"></a>.Vsct 文件设计准则  
 若要成功设计.vsct 文件，请遵循以下准则。  
  
-   命令可以放在组中仅、 组可以放置仅在菜单和菜单可以放置仅在组中。 仅菜单实际显示在 IDE 中，组和命令不可。  
  
-   子菜单不能直接分配到的菜单中，但必须分配给一个组，将依次分配到的菜单。  
  
-   命令、 子菜单和组可以分配给一个父级组或使用其定义的指令的父字段的菜单。  
  
-   组织的指令中的父字段只能通过命令表具有一个明显的限制。 定义对象的指令可以采用只有一个父自变量。  
  
-   重复使用命令、 组或子菜单需要一个新的指令，用于创建具有其自己的对象的新实例使用`GUID:ID`对。  
  
-   每个`GUID:ID`对必须是唯一的。 重复使用，例如，已放在菜单上，一个工具栏，或在上下文菜单上，命令由处理<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口。  
  
-   命令和子菜单还可以分配给多个组，并且组可以分配到多个菜单使用[命令元素](../../extensibility/commands-element.md)。  
  
## <a name="vsct-file-notes"></a>.Vsct 文件说明  
 如果你同时对其进行编译，并将其放在本机附属 DLL 后，可以对.vsct 文件进行任何更改，则应运行**devenv.exe /setup /nosetupvstemplates**。 执行此操作强制在实验注册表以重新读取和描述的内部数据库中指定的 VSPackage 资源[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]重新生成。  
  
 在开发期间，很可能为多个 VSPackage 项目以创建和注册在实验注册表配置单元可能导致令人困惑在 IDE 中的混乱程度。 要解决此问题，你可以为默认设置，以删除所有已注册的 Vspackage 和它们可能对 IDE 所做任何更改将实验性配置单元。 若要重置实验性配置单元，请使用 Visual Studio SDK 随附的 CreateExpInstance.exe 工具。 你可以找到它在  
  
 **%Programfiles (x86) %\Visual Studio\<版本 > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 通过使用命令行运行该工具**CreateExpInstance /Reset**。 请记住，此工具会从实验性配置单元通常不被安装的所有已注册的 Vspackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [扩展菜单和命令](../../extensibility/extending-menus-and-commands.md)