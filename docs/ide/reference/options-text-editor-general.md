---
title: "选项，文本编辑器，常规 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL"
  - "VS.ToolsOptionsPages.Text_Editor.All_Languages.General"
  - "VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General"
  - "VS.ToolsOptionsPages.Text_Editor.SQL.General"
  - "vs.toolsoptionspages.text_editor"
  - "VS.ToolsOptionsPages.Text_Editor.XML.General"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL80.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSS"
  - "VS.ToolsOptionsPages.Text_Editor.Plain_Text.General"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.General"
  - "VS.ToolsOptionsPages.Text_Editor.SQL_Script.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.General"
  - "VS.ToolsOptionsPages.Text_Editor.All_Languages"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL7.General"
  - "VS.ToolsOptionsPages.Text_Editor.Basic.General"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL.General"
  - "vs.toolsoptionspages.text_editor.visual_jsharp"
  - "VS.ToolsOptionsPages.Text_Editor.F#.Tabs"
  - "VS.ToolsOptionsPages.Text_Editor.F#"
  - "VS.ToolsOptionsPages.Text_Editor.PL/SQL.General"
  - "VS.ToolsOptionsPages.Text_Editor.C/C++.General"
  - "VS.ToolsOptionsPages.Text_Editor.Plain_Text"
  - "VS.ToolsOptionsPages.Text_Editor.HTML"
  - "VS.ToolsOptionsPages.Text_Editor.XAML.General"
  - "VS.ToolsOptionsPages.Text_Editor"
  - "VS.ToolsOptionsPages.Text_Editor.F#.General"
  - "VS.ToolsOptionsPages.Text_Editor.XOML.General"
  - "VS.ToolsOptionsPages.Text_Editor.SQL"
  - "vs.toolsoptionspages.text_editor.c/c++"
  - "VS.ToolsOptionsPages.Text_Editor.SQL_Script"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL90.General"
  - "VS.ToolsOptionsPages.Text_Editor.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp"
helpviewer_keywords: 
  - "“文本编辑器选项”对话框"
  - "代码编辑器"
  - "文本编辑器 [Visual Studio]"
  - "编辑器，全局设置"
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# 选项，文本编辑器，常规
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用此对话框可以更改 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 代码和文本编辑器的全局设置。  若要显示此对话框，请单击**“工具”**菜单上的**“选项”**，展开**“文本编辑器”**文件夹，然后单击**“常规”**。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于您现用的设置或版本。  若要更改设置，请在**“工具”**菜单上选择**“导入和导出设置”**。  有关更多信息，请参见[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 设置  
 拖放文本编辑  
 选定后，您可以通过用鼠标选定文本并将其拖到当前文档或任何其他打开的文档中的其他位置来移动文本。  
  
 自动突出显示分隔符  
 选定后，将突出显示分开参数或项值对的分隔符以及匹配括号。  
  
 修订  
 在代码编辑器中选择时，一个垂直黄色的行出现在选择边距指示已更改的代码，则最近保存该文件。  当保存更改时，竖线变为绿色。  
  
 自动检测不带签名的 UTF\-8 编码  
 默认情况下，编辑器通过搜索字节顺序标记或字符集标记来检测编码。  如果在当前文档中两者均未找到，代码编辑器将尝试通过扫描字节序列来自动检测 UTF\-8 编码。  若要禁用自动编码检测，请清除此选项。  
  
## 显示  
 选定内容的边距  
 选定后，将沿着编辑器文本区左边缘显示一条垂直边距。  您可以单击此边距以选择一整行文本，或者单击并拖动以选择多行连续的文本。  
  
|打开选定内容的边距|关闭选定内容的边距|  
|---------------|---------------|  
|![HTMLpageSelectionMarginOn 屏幕快照](../../ide/reference/media/vxselmaron.png "vxSelmaron")|![HTMLpageSelectionMarginOff 屏幕快照](../../ide/reference/media/vxselmaroff.gif "vxSelmaroff")|  
  
 指示器边距  
 选定后，在编辑器文本区左边缘的外部显示一个垂直边距。  在此边距内单击时，会显示与文本有关的图标和工具提示。  例如，断点或任务列表快捷方式显示在指示器边距内。  指示器边距信息打印不出来。  
  
 垂直滚动条  
 选定后，会显示一个垂直滚动条，供您上下滚动查看位于编辑器可视区域外的元素。  如果没有垂直滚动条，可使用 PAGE UP、PAGE DOWN 键和光标键滚动。  
  
 水平滚动条  
 选定后，会显示一个水平滚动条，供您左右滚动查看位于编辑器可视区域外的元素。  若没有水平滚动条，可使用光标键滚动。  
  
 突出显示当前行  
 如果选择此选项，则会显示一条灰色框在光标代码周围的行。  
  
## 请参阅  
 [选项、文本编辑器、所有语言](../../ide/reference/options-text-editor-all-languages.md)   
 [选项，文本编辑器，所有语言，选项卡](../../ide/reference/options-text-editor-all-languages-tabs.md)   
 [选项，文本编辑器，文件扩展名](../../ide/reference/options-text-editor-file-extension.md)   
 [标识并自定义键盘快捷键](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)   
 [自定义编辑器](../../ide/customizing-the-editor.md)   
 [使用 IntelliSense](../../ide/using-intellisense.md)