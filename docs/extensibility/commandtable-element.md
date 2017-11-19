---
title: "CommandTable 元素 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d4f1a906f545dcdbaefca7f5a38824a1f3259c97
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="commandtable-element"></a>CommandTable 元素
CommandTable 是.vsct 文件的根元素。 这是定义的实际布局和 VSPackage 提供给 IDE 的命令的类型的文件。 命令可能包括菜单项、 菜单、 工具栏和组合框。 有关详细信息，请参阅 [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
## <a name="syntax"></a>语法  
  
```  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >  
  <Extern>... </Extern>  
  <Include>... </Include>  
  <Define>... </Define>  
  <Commands>... </Commands>  
  <CommandPlacements>... </CommandPlacements>  
  <VisibilityConstraints>... </VisibilityConstraints>  
  <KeyBindings>... </KeyBindings>  
  <UsedCommands... </UsedCommands>  
  <Symbols>... </Symbols>  
</CommandTable>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|xmlns|必需。 XML 命名空间：<br /><br /> xmlns ="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"<br /><br /> xmlns:xs ="http://www.w3.org/2001/XMLSchema"|  
|语言|可选。 Language 特性可用于指定的默认语言的所有\<字符串 > 命令表中的元素。  如果未指定语言，则将使用当前进程的语言：<br /><br /> 语言 ="en-我们"|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[Extern 元素](../extensibility/extern-element.md)|可选。 包含用于编译器预处理器指令。|  
|[ Include元素](../extensibility/include-element.md)|可选。 包含指向要包含在编译中的任何文件路径。|  
|[Define 元素](../extensibility/define-element.md)|可选。 定义在给定其名称和值的符号。|  
|[Commands 元素](../extensibility/commands-element.md)|可选。 父元素为包含的所有其他元素的 VSPackage 定义的所有命令。|  
|[CommandPlacements 元素](../extensibility/commandplacements-element.md)|可选。 定义命令栏上的命令的位置以放置。|  
|[VisibilityConstraints 元素](../extensibility/visibilityconstraints-element.md)|可选。 确定命令和工具栏的静态的可见。|  
|[KeyBindings 元素](../extensibility/keybindings-element.md)|可选。 如果任何命令，则指定快捷组合键。|  
|[UsedCommands 元素](../extensibility/usedcommands-element.md)|可选。 允许 VSPackage 来选择实现其自己的版本的最初受其他 Vspackage 的功能。|  
|[Symbols 元素](http://msdn.microsoft.com/en-us/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|可选。 包含编译器任何符号数据 （Guid、 Id 和等）。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|无||  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 命令表格 (.Vsct) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)