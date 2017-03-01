---
title: "CommandTable 元素 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: 11
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
ms.openlocfilehash: 4a6abf25d0e3eff335c8a6fe62affc19d8037afa
ms.lasthandoff: 02/22/2017

---
# <a name="commandtable-element"></a>CommandTable 元素
CommandTable 是.vsct 文件的根元素。 这是定义的实际布局和向 IDE 提供 VSPackage 命令类型的文件。 命令可能包括菜单项、 菜单、 工具栏和组合框。 有关详细信息，请参阅[Visual Studio 命令表 (。Vsct) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
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
|xmlns|必需。 XML 命名空间︰<br /><br /> xmlns ="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"<br /><br /> xmlns:xs ="http://www.w3.org/2001/XMLSchema"|  
|语言|可选。 语言特性可用于指定的默认语言的所有\<字符串&1;> 命令表中的元素。  如果未指定语言，则将使用当前进程的语言︰<br /><br /> 语言 ="en-我们"|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[Extern 元素](../extensibility/extern-element.md)|可选。 包含用于编译器预处理器指令。|  
|[Include 元素](../extensibility/include-element.md)|可选。 包含要包含在编译中的任何文件的路径。|  
|[定义元素](../extensibility/define-element.md)|可选。 定义在给定其名称和值的符号。|  
|[Commands 元素](../extensibility/commands-element.md)|可选。 父元素定义的所有命令的 VSPackage，其中包含所有其他元素。|  
|[CommandPlacements 元素](../extensibility/commandplacements-element.md)|可选。 定义了在何处在命令栏命令应放。|  
|[VisibilityConstraints 元素](../extensibility/visibilityconstraints-element.md)|可选。 确定静态可见性命令和工具栏。|  
|[键绑定元素](../extensibility/keybindings-element.md)|可选。 指定快捷组合键，如果有，这些命令。|  
|[UsedCommands 元素](../extensibility/usedcommands-element.md)|可选。 允许根据需要实现其自己的版本的最初由其他 VSPackages 迁移支持的功能的 VSPackage。|  
|[符号元素](http://msdn.microsoft.com/en-us/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|可选。 包含编译器任何符号数据 （Guid、 Id 和等）。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|无||  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 命令表 (。Vsct) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
