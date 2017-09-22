---
title: "“选项”->“文本编辑器”->“C#”->“格式设置”| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting
helpviewer_keywords:
- formatting [C#]
- formatting [J#]
- Text Editor Options dialog box, formatting
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
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
ms.openlocfilehash: a157bb6b5e29bb90fcd033f58657887f610b4835
ms.contentlocale: zh-cn
ms.lasthandoff: 05/24/2017

---
# <a name="options-text-editor-c-formatting"></a>选项、文本编辑器、C#、格式设置
使用“格式设置”属性页对话框可以在代码编辑器中设置格式设置代码的选项。 若要访问此对话框，请单击“工具”菜单上的“选项”，展开“文本编辑器”，再展开“C#”，然后单击“格式设置”。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="general-settings"></a>常规设置  
 常规设置影响代码编辑器将格式设置选项应用于代码的方式。  
  
## <a name="uielement-list"></a>UIElement 列表  
  
|标签|描述|  
|-----------|-----------------|  
|**输入 ; 时自动设置已完成语句的格式**|如果选中此项，会根据为代码编辑器选择的格式设置选项在完成时对语句进行格式设置。 如果不希望代码编辑器更改语句，请清除此框。|  
|**输入 } 时自动设置已完成块的格式**|如果选中此项，完成代码块后，立即根据为代码编辑器选择的格式设置选项设置代码块的格式。 如果不希望代码编辑器更改代码块，请清除此框。|  
|**粘贴文本时调整缩进**|如果选中该选项，则设置粘贴到代码编辑器中的文本的格式，以匹配为代码编辑器选择的格式设置选项。 如果不希望更改粘贴的文本，则清除此框。|  
  
## <a name="preview-window"></a>预览窗口  
 “缩进”、“新行”、“间距”和“包装”选项窗格都会显示一个预览窗口。 预览窗口显示每个选项的效果。 若要使用预览窗口，请选择一个格式设置选项。 预览窗口显示选定选项的示例。 更改设置（例如选中或清除复选框）时，预览窗口将会更新，显示新设置的效果。  
  
## <a name="remarks"></a>备注  
 每种语言下，“选项卡”页的缩进选项仅确定你在行末按 Enter 时，代码编辑器将光标置于何处。 在自动设置代码的格式时应用“格式设置”下的缩进选项，例如，在选定“粘贴时调整缩进”时将代码粘贴到文件中时，以及手动键入要设置格式的代码块时。  
  
## <a name="see-also"></a>另请参阅  
 [“选项”对话框 ->“环境”->“常规”](../../ide/reference/general-environment-options-dialog-box.md)
