---
title: "选项、文本编辑器、C#、格式设置 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.NewLines"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Indentation"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Wrapping"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Spacing"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting"
helpviewer_keywords: 
  - "格式设置 [C#]"
  - "格式设置 [J#]"
  - "“文本编辑器选项”对话框，格式设置"
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# 选项、文本编辑器、C#、格式设置
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用**“格式设置”**属性页对话框可以在代码编辑器中设置格式设置代码的选项。  若要访问此对话框，请单击**“工具”**菜单上的**“选项”**，展开**“文本编辑器”**，再展开**“C\#”**，然后单击**“格式设置”**。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于您现用的设置或版本。  若要更改设置，请在**“工具”**菜单上选择**“导入和导出设置”**。  有关详细信息，请参阅 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 常规设置  
 常规设置影响代码编辑器将格式设置选项应用于代码的方式。  
  
## UIElement 列表  
  
|Label|描述|  
|-----------|--------|  
|**自动设置 ; 上已完成语句的格式**|如果选中，则根据为代码编辑器选择的格式设置选项在完成时对语句进行格式设置。  如果不希望代码编辑器改变语句，则清除此框。|  
|**自动设置 } 上已完成块的格式**|如果选择该选项，完成代码块后立即根据为代码编辑器选择的格式设置选项设置该代码块的格式。  如果不希望代码编辑器改变代码块，则清除此框。|  
|**粘贴时调整缩进**|如果选择该选项，则设置粘贴到代码编辑器中的文本的格式，以适合为代码编辑器选择的格式设置选项。  如果不希望改变粘贴的文本，则清除此框。|  
  
## “预览”窗口  
 **“缩进”**、**“新行”**、**“间距”**和**“换行”**选项窗格都显示一个预览窗口。  预览窗口显示每个选项的效果。  若要使用预览窗口，请选择一个格式设置选项。  预览窗口显示选定选项的示例。  当更改设置时（例如选中或清除复选框），预览窗口将会更新以显示新设置的效果。  
  
## 备注  
 每种语言的**“制表符”**页上的缩进选项仅确定在行尾按 Enter 时代码编辑器放置光标的位置。  在自动设置代码的格式时应用**“格式设置”**下的缩进选项，例如，在选定**“粘贴时调整缩进”**时将代码粘贴到文件中时，以及手动键入要设置格式的代码块时。  
  
## 请参阅  
 [“选项”对话框 \-\>“环境”\-\>“常规”](../../ide/reference/general-environment-options-dialog-box.md)