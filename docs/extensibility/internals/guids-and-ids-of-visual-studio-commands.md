---
title: "Guid 和 Id 的 Visual Studio 命令 | Microsoft Docs"
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
  - "命令"
  - "id"
  - "命令放置"
  - "visual studio 命令"
  - "guid"
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# Guid 和 Id 的 Visual Studio 命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在 Visual Studio 集成开发环境 \(ide\) 包含的命令的 GUID 和 ID 值 \(IDE\)在为 Visual Studio SDK 的一部分，安装的 .vsct 文件中定义的。  有关更多信息，请参见 [IDE 定义的命令、 菜单和组](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)。  
  
 有关如何安装的更多信息与 .vsct 文件中定义的 IDE 对象，请参见 [扩展的菜单和命令](../../extensibility/extending-menus-and-commands.md)。  
  
## 查找顺序定义  
 由于 Visual Studio 定义多个数千个命令，列出它们全部此处不可行。  相反，请按照以下步骤找到命令的定义。  
  
#### 找到命令定义  
  
1.  在 Visual Studio 中，打开在 *Visual Studio SDK 安装路径*\\VisualStudioIntegration\\Common\\Inc\\ folder: SharedCmdDef.vsct， ShellCmdDef.vsct， VsDbgCmdUsed.vsct， Venusmenu .vsct 的以下文件。  
  
     大多数 Visual Studio 命令在 SharedCmdDef.vsct 和 ShellCmdDef.vsct 定义。  VsDbgCmdUsed.vsct 定义与调试器的命令，并且， Venusmenu.vsct 定义特定于 Web 开发的命令。  
  
2.  如果命令是菜单项，请注意菜单项的确切文本。  如果命令是工具栏上的按钮，请注意显示的工具提示文本在停放在。  
  
3.  按 CTRL\+F 打开 **查找** 对话框。  
  
4.  在 **" 查找内容 "** 框中，键入您在步骤中指出的文本。  
  
5.  验证 **所有打开的文档** 在 **查找** 将显示框。  
  
6.  单击 **查找下一个** 按钮，直到该文本将 [Button 元素](../../extensibility/button-element.md)的 `<Strings>` 节中选择。  
  
     命令显示的 `<Button>` 元素是命令定义。  
  
 当您找到命令定义时，可以在另一个菜单或工具栏上可以将命令将副本传递具有 `guid` 和 `id` 值和命令相同的创建 [CommandPlacement 元素](../../extensibility/commandplacement-element.md) 。  有关更多信息，请参见 [创建可重用的按钮的组](../../extensibility/creating-reusable-groups-of-buttons.md)。  
  
### 特殊情况  
 在以下情况下，菜单文本或工具提示文本可能不完全匹配任何命令定义。  
  
-   包括带下划线的字符，如 **文件** 菜单的 **打印** 命令， P 带下划线的菜单项。  
  
     在菜单项名称 "  字符后面的字符显示为带有下划线。  但是， .vsct 文件在 XML 中，使用 "  字符指示特殊字符并调用以显示必须清楚地说明了 "  的 " and " 符。  因此，在 .vsct 文件，打印顺序出现 "  。  
  
-   具有动态文本，例如 **保存** *当前文件名*和动态生成的菜单项的命令，如 **最近的文件** 的项列表。  
  
     没有可靠的方式搜索在动态文本。  相反，查找由查询的 [Guid 和 Id 的 Visual Studio 菜单](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) 或 [Guid 和 Id 的 Visual Studio 工具栏](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)承载所需的命令的一该组 ID 的组和搜索。  如果命令定义没有组作为其 [父元素](../../extensibility/parent-element.md)，搜索 SharedCmdPlace.vsct 和 ShellCmdPlace.vsct \(或 VsDbgCmdPlace.vsct 调试器命令\) 将该命令的父级的 `<CommandPlacement>` 元素。  SharedCmdPlace.vsct， ShellCmdPlace.vsct， andVsDbgCmdPlace.vsct 在 *Visual Studio SDK 安装路径*\\VisualStudioIntegration\\Common\\Inc \\ 文件夹。  
  
## 请参阅  
 [MenuCommands 与 OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Visual Studio 命令表 \(。Vsct\) 文件](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML 架构参考](../../extensibility/vsct-xml-schema-reference.md)