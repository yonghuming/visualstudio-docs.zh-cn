---
title: "Guid 和 Id 的 Visual Studio 命令 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ce546f36ed93f0f42bfd548c64f2a25669e162b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Guid 和 Id 的 Visual Studio 命令
在 Visual Studio SDK 的一部分安装的.vsct 文件定义包含在 Visual Studio 集成的开发环境 (IDE) 中的命令的 GUID 和 ID 值。 有关详细信息，请参阅[IDE-Defined 命令、 菜单和组](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)。  
  
 有关如何使用 IDE 对象，在.vsct 文件中定义的详细信息，请参阅[扩展菜单和命令](../../extensibility/extending-menus-and-commands.md)。  
  
## <a name="finding-a-command-definition"></a>查找命令定义  
 Visual Studio 定义多个一千命令，因为它是不切实际其所有此处列出的。 相反，请按照下列步骤以查找命令的定义。  
  
#### <a name="to-locate-a-command-definition"></a>若要查找命令定义  
  
1.  在 Visual Studio 中，打开中的以下文件*Visual Studio SDK 安装路径*\VisualStudioIntegration\Common\Inc\ 文件夹： SharedCmdDef.vsct、 ShellCmdDef.vsct、 VsDbgCmdUsed.vsct、 Venusmenu.vsct。  
  
     大多数 Visual Studio 命令 SharedCmdDef.vsct 和 ShellCmdDef.vsct 中定义。 VsDbgCmdUsed.vsct 定义适用于调试程序时，命令而 Venusmenu.vsct 定义特定于 Web 开发的命令。  
  
2.  如果该命令是菜单项，记下的菜单项的确切文本。 如果该命令是一个工具栏上的按钮，请注意当你将鼠标悬停在其上时显示的工具提示文本。  
  
3.  按 CTRL + F 来打开**查找**对话框。  
  
4.  在**查找内容**框中，键入在步骤 2 中记下的文本。  
  
5.  验证**所有打开的文档**中显示**查找**框。  
  
6.  单击**查找下一个**按钮，直到中选定该文本`<Strings>`部分[Button 元素](../../extensibility/button-element.md)。  
  
     `<Button>`命令显示中的元素是命令定义。  
  
 当时已找到命令定义，你可以将命令的副本在另一个菜单或工具栏上通过创建[CommandPlacement 元素](../../extensibility/commandplacement-element.md)具有相同`guid`和`id`作为命令的值。 有关详细信息，请参阅[按钮创建可重用组](../../extensibility/creating-reusable-groups-of-buttons.md)。  
  
### <a name="special-cases"></a>特殊情况  
 在以下情况下，菜单文本或工具提示文本可能不完全匹配中的命令定义。  
  
-   包括带下划线的字符，如的菜单项**打印**命令**文件**菜单上，P 是否有下划线。  
  
     前面带有菜单项名称中的 & 字符的字符显示为带下划线。 但是，在 XML 中，也不能使用 & 字符来指示特殊字符需要，应显示 and 符必须拼编写.vsct 文件为&amp;。 因此，在.vsct 文件中， **P**rint 命令显示为&amp;打印。  
  
-   具有动态文本，如命令**保存***当前文件名*，和动态生成上的菜单项，如项**最近使用的文件**列表。  
  
     没有可靠的方法来搜索动态文本。 相反，查找通过参考承载所需的命令的组[Guid 和 Id 的 Visual Studio 菜单](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)或[Guid 和 Id 的 Visual Studio 工具栏](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)，和搜索该组的 ID。 如果命令定义没有组作为其[父元素](../../extensibility/parent-element.md)，搜索 SharedCmdPlace.vsct 和 ShellCmdPlace.vsct （或调试器命令 VsDbgCmdPlace.vsct）`<CommandPlacement>`设置的父级的元素命令。 SharedCmdPlace.vsct，ShellCmdPlace.vsct，andVsDbgCmdPlace.vsct 位于*Visual Studio SDK 安装路径*\VisualStudioIntegration\Common\Inc\ 文件夹。  
  
## <a name="see-also"></a>另请参阅  
 [MenuCommands 与OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Visual Studio 命令表 (。Vsct) 文件](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML 架构参考](../../extensibility/vsct-xml-schema-reference.md)