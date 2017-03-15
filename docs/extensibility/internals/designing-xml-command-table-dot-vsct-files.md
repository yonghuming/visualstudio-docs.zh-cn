---
title: "设计 XML 命令表 (。Vsct) 文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: 27
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 047c23f9571007870e6d4db50f4604713c0d7ea3
ms.lasthandoff: 02/22/2017

---
# <a name="designing-xml-command-table-vsct-files"></a>设计 XML 命令表 (。Vsct) 文件
XML 命令表 (.vsct) 文件描述的布局和为 VSPackage 命令项的外观。 命令项包括按钮、 组合框、 菜单、 工具栏和命令项的组。 本主题介绍 XML 命令表文件、 它们如何影响命令项目和菜单，以及如何创建它们。  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>命令、 菜单、 组和.vsct 文件  
 .vsct 文件组织周围命令、 菜单和命令组中。 在.vsct 文件中的 XML 标记表示每个这些项，以及其他相关联的项，如命令按钮、 命令放置和位图。  
  
 通过运行时创建新的 VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]包模板，该模板会生成具有必需的元素的菜单命令、 工具窗口中或自定义编辑器中的，具体取决于您选择的.vsct 文件。 然后可以修改此.vsct 文件以满足特定的 VSPackage 的要求。 有关如何修改.vsct 文件的示例，请参阅中的示例[扩展菜单和命令](../../extensibility/extending-menus-and-commands.md)。  
  
 若要创建新的空白.vsct 文件时，请参阅[如何︰ 创建。Vsct 文件](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)。 创建后，您将添加 XML 元素、 属性和值到文件来描述命令项布局。 有关详细的 XML 架构，请参阅[VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md)。  
  
## <a name="differences-between-ctc-and-vsct-files"></a>.Ctc 和.vsct 文件之间的差异  
 虽然.vsct 文件中的 XML 标记背后的含义是相同的为参与了现已弃用.ctc 文件格式，其实现是略有不同。  
  
-   新** \<extern&1;>**标记是，引用其他.h 文件，以便进行编译，例如，那些用于[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]工具栏。  
  
-   虽然.vsct 文件支持**/ 包括**语句中，在进行.ctc 文件，它还提供了一个新\<**导入&1;>**元素。 其差异是， **/ 包括**中将引入**所有**的信息，但\<**导入&1;>**中只有名称的名称将引入。  
  
-   虽然.ctc 文件需要在其中定义预处理器指令的标头文件，不需要为.vsct 文件。 相反，将您指令放置在符号表中，位于**\<符号&1;>**元素，位于.vsct 文件的底部。  
  
-   .vsct 文件功能**\<注释&1;>**标记，它使您可以嵌入任何您喜欢，如说明或甚至图片的信息。  
  
-   作为在项上的属性存储值。  
  
-   可以单独存储或堆积命令标志。  Intellisense，但是，不会无法正常工作对堆积的命令标志。 有关命令标志的详细信息，请参阅[命令标志元素](../../extensibility/command-flag-element.md)。  
  
-   您可以指定多个类型，例如拆分下拉框、 组合等。  
  
-   Guid 不会验证。  
  
-   每个 UI 元素具有一个字符串，表示与它一起显示的文本。  
  
-   父级是可选的。 如果省略，则使用"组未知"的值。  
  
-   图标参数是可选的。  
  
-   将文件位图部分-.ctc 相同，只不过现在可以指定一个文件名，通过将由 vsct.exe 编译器抽取在编译时的 href。  
  
-   ResID-将旧的位图资源 ID 可以使用，如下所示.ctc 文件仍的工作方式相同。  
  
-   HRef — 一个新的方法，允许您指定的位图资源的文件名。 它假定将使用所有，因此可以省略使用部分。 首先，编译器将搜索该文件，然后在任何网络共享上的本地资源和定义/I 开关的任何资源。  
  
-   键绑定-不再需要指定一个仿真程序。 如果您指定一个，则编译器将假定编辑器和仿真程序都相同。  
  
-   Keychord-已被删除。 新的格式是 Key1、 Mod1、 Key2、 Mod2。  您可以指定字符、 十六进制、 或 VK 常量。  
  
 新的编译器、 vsct.exe，编译.ctc 和.vsct 文件。 旧的 ctc.exe 编译器，但是，将不识别或编译.vsct 文件。  
  
 Vsct.exe 编译器用于将现有.cto 文件转换为.vsct 文件。 有关更多相关信息，请参阅[如何︰ 创建。从现有 Vsct 文件。首席技术官文件](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)。  
  
## <a name="the-vsct-file-elements"></a>.Vsct 文件元素  
 命令表具有以下层次结构和元素︰  
  
 [CommandTable 元素](../../extensibility/commandtable-element.md)— 表示的所有命令、 菜单组和 VSPackage 与关联的菜单。  
  
 [Extern 元素](../../extensibility/extern-element.md)— 引用您想要与.vsct 文件合并任何外部.h 文件。  
  
 [包含元素](../../extensibility/include-element.md)— 引用您想要编译 your.vsct 文件以及任何其他标头 (.h) 文件。 .Vsct 文件可以包含.h 文件，其中包含定义 IDE 或另一个 VSPackage 所提供的命令、 菜单组和菜单的常量。  
  
 [命令元素](../../extensibility/commands-element.md)— 表示所有可执行的单个命令。 每个命令具有以下四个子元素︰  
  
 [菜单元素](../../extensibility/menus-element.md)— 表示所有的菜单和工具栏在 VSPackage 中的。 菜单是组的命令的容器。  
  
 [Groups 元素](../../extensibility/groups-element.md)— 表示所有 VSPackage 中的组。 组是单独命令的集合。  
  
 [按钮元素](../../extensibility/buttons-element.md)— 表示所有的命令按钮和菜单项在 VSPackage。 按钮是可以与命令相关联的可视控件。  
  
 [位图元素](../../extensibility/bitmaps-element.md)— 表示所有 VSPackage 中的按钮的所有位图。 位图是显示下一步或上的命令按钮，具体取决于上下文的图片。  
  
 [CommandPlacements 元素](../../extensibility/commandplacements-element.md)-指示你的 VSPackage 的菜单中的各个命令应位于其中的其他位置。  
  
 [VisibilityConstraints 元素](../../extensibility/visibilityconstraints-element.md)-指定是否命令将显示在所有时间，或仅在某些上下文中，例如显示特定的对话框或窗口时。 仅在指定的上下文处于活动状态时，将显示菜单和命令具有此元素的值。 默认行为是可在任何时候显示命令。  
  
 [键绑定元素](../../extensibility/keybindings-element.md)— 指定任何键绑定命令。 也就是说，一个或多个键组合必须按下要执行该命令，如**CTRL + S**。  
  
 [UsedCommands 元素](../../extensibility/usedcommands-element.md)— 通知[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，虽然当前 VSPackage 处于活动状态时，将由其他代码，实现指定的命令，但它提供了命令实现的环境。  
  
 `Symbols Element`-包含的符号名称和 GUID 所有您在包中的命令 Id。  
  
## <a name="vsct-file-design-guidelines"></a>.Vsct 文件设计指导原则  
 若要成功设计.vsct 文件，请遵循以下准则。  
  
-   命令可以放置仅在组中、 组可以放置仅在菜单和菜单可以放置仅在组中。 仅菜单实际显示在 IDE 中，组和命令都不。  
  
-   子菜单不能直接分配到菜单上，但必须将分配给一个组，将依次分配到菜单。  
  
-   命令、 子菜单和组可以分配给一个父级组或使用其定义的指令的父字段的菜单。  
  
-   组织只通过父字段的指令中的命令表有一个明显的限制。 定义对象的指令可以只有一个父参数。  
  
-   重复使用的命令、 组或子菜单需要使用新的指令以创建该对象的新实例具有自己`GUID:ID`对。  
  
-   每个`GUID:ID`对都必须唯一。 重复使用的命令，例如，已放在菜单上，一个工具栏，或在上下文菜单中，由处理<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口。</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>  
  
-   命令和子菜单也可分配到多个组和组可以分配给多个菜单使用[Commands 元素](../../extensibility/commands-element.md)。  
  
## <a name="vsct-file-notes"></a>.Vsct 文件说明  
 如果在同时对其进行编译，并将其放置在本机附属 DLL 之后，可以对.vsct 文件进行任何更改，则应运行**devenv.exe /setup /nosetupvstemplates**。 执行此操作将强制在实验性的注册表，以重新读取和描述的内部数据库中指定的 VSPackage 资源[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]重新生成。  
  
 在开发期间，就可以对多个 VSPackage 项目，若要创建和注册可能会导致令人困惑的混乱，在 IDE 中的实验性的注册表配置单元中。 若要解决此问题，可以重实验 hive 置为默认设置，若要删除所有已注册的 VSPackages 迁移和可能对 IDE 进行的任何更改。 若要重置实验配置单元，请使用附带了 Visual Studio SDK 的 CreateExpInstance.exe 工具。 你可以找到它在  
  
 **%Programfiles (x86) %\Visual Studio\<版本&1;> SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 通过使用命令行运行该工具**CreateExpInstance /Reset**。 请记住，此工具会移除从实验配置单元通常不与安装的所有已注册的 Vspackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [扩展的菜单和命令](../../extensibility/extending-menus-and-commands.md)
