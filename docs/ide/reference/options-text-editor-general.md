---
title: "“选项”->“文本编辑器”->“常规”| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.XML.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
- VS.ToolsOptionsPages.Text_Editor.CSS
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- vs.toolsoptionspages.text_editor.visual_jsharp
- VS.ToolsOptionsPages.Text_Editor.F#.Tabs
- VS.ToolsOptionsPages.Text_Editor.F#
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text
- VS.ToolsOptionsPages.Text_Editor.HTML
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.XOML.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- vs.toolsoptionspages.text_editor.c/c++
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.CSharp
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
caps.latest.revision: 29
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: eee3b34e9f473c200463b65f1b839416f5dce0ec
ms.contentlocale: zh-cn
ms.lasthandoff: 05/24/2017

---
# <a name="options-text-editor-general"></a>选项，文本编辑器，常规
使用此对话框可以更改 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 代码和文本编辑器的全局设置。 若要显示此对话框，请在“工具”菜单上单击“选项”，展开“文本编辑器”文件夹，然后单击“常规”。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="settings"></a>设置  
 拖放文本编辑  
 勾选此项后，使用鼠标选定文本并将其拖到当前文档的其他位置或任何其他打开的文档中，即可移动文本。  
  
 自动突出显示分隔符  
 勾选此项后，将突出显示分隔参数、项值对以及成对大括号的分隔符字符。  
  
 跟踪更改  
 选定代码编辑器后，所选内容的边距中会出现一条垂直的黄线，标记自文件上次保存后更改的代码。 保存更改时，竖线变为绿色。  
  
 自动检测不带签名的 UTF-8 编码  
 默认情况下，编辑器通过搜索字节顺序标记或字符集标记检测编码。 如果在当前文档中两者均未找到，代码编辑器将尝试通过扫描字节序列，自动检测 UTF-8 编码。 若要禁用自动检测编码，请清除此选项。  
  
## <a name="display"></a>显示  
 选定内容的边距  
 勾选此项后，将显示编辑器文本区域的左侧边缘的垂直边距。 可以通过单击此边距选择一整行文本，或者通过单击并拖动，选择连续多行文本。  
  
|打开选定内容的边距|关闭选定内容的边距|  
|-------------------------|--------------------------|  
|![HTMLpageSelectionMarginOn 屏幕截图](~/docs/ide/reference/media/vxselmaron.gif "vxSelmaron")|![HTMLpageSelectionMarginOff 屏幕截图](~/docs/ide/reference/media/vxselmaroff.gif "vxSelmaroff")|  
  
 指示器边距  
 勾选此项后，将显示编辑器文本区域的左侧边缘外的垂直边距。 在此边距内单击时，会显示与文本有关的图标和工具提示。 例如，指示器边距内会出现断点或任务列表快捷方式。 但不显示指示器边距信息。  
  
 垂直滚动条  
 勾选此项后，会显示一个垂直滚动条，用户可以上下滚动，查看编辑器查看区域外的元素。 如果垂直滚动条不可用，可以使用 Page Up、Page Down 键和光标键滚动。  
  
 水平滚动条  
 勾选此项后，会显示一个水平滚动条，用户可以左右滚动，查看编辑器查看区域外的元素。 如果水平滚动条不可用，可以使用光标键滚动。  
  
 突出显示当前行  
 勾选此项后，光标所在代码行周围会显示一个灰色框。  
  
## <a name="see-also"></a>另请参阅  
 [“选项”->“文本编辑器”->“所有语言”](../../ide/reference/options-text-editor-all-languages.md)   
 [“选项”->“文本编辑器”->“所有语言”->“制表符”](../../ide/reference/options-text-editor-all-languages-tabs.md)   
 [“选项”->“文本编辑器”->“文件扩展名”](../../ide/reference/options-text-editor-file-extension.md)   
 [标识并自定义键盘快捷方式](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)   
 [自定义编辑器](../../ide/customizing-the-editor.md)   
 [使用 IntelliSense](../../ide/using-intellisense.md)
