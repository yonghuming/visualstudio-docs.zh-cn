---
title: "选项，文本编辑器，C#，IntelliSense | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Intellisense
helpviewer_keywords:
- IntelliSense [J#], options
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ac32cd3946e6d244f6ff658bb636c9ecfd89e197
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="options-text-editor-c-intellisense"></a>选项，文本编辑器，C#，IntelliSense
使用“IntelliSense”属性页可以修改影响 IntelliSense for Visual C# 行为的设置。 通过单击“工具”菜单上的“选项”，再单击“文本编辑器”文件夹中的“C#”，然后单击“IntelliSense”，可以访问“IntelliSense”属性页。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../../ide/personalizing-the-visual-studio-ide.md)。  
  
 “IntelliSense”属性页包含下列属性：  
  
## <a name="completion-lists"></a>完成列表  
 **键入字符后显示完成列表**  
 选择此选项后，IntelliSense 在你开始键入时会自动显示完成列表。 未选择此选项时，仍可从“IntelliSense”菜单或通过按 Ctrl+空格来使用 IntelliSense 完成功能。  
  
 **将关键字放入完成列表**  
 选择此选项后，IntelliSense 会将 C# 关键字（例如 [class](/dotnet/csharp/language-reference/keywords/class)）添加到完成列表中。  
  
 **将代码片段放入完成列表**  
 选择此选项后，IntelliSense 将 C# 代码片段的别名添加到完成列表中。 如果代码片段别名与关键字相同（例如均为 [class](/dotnet/csharp/language-reference/keywords/class)），则快捷方式将替代关键字。 有关详细信息，请参阅 [Visual C#代码片段](../../ide/visual-csharp-code-snippets.md)。  
  
## <a name="selection-in-completion-lists"></a>完成列表中的选定内容  
 **通过键入以下字符提交：**  
 指定键入完成列表中选定项后执行 IntelliSense 自动完成的所有字符。  
  
 **通过按空格键提交**  
 指定包含这样一个操作：按空格键即为完成列表中的选定项执行 IntelliSense 自动完成。  
  
 **在完整键入的字末尾按 Enter 添加新行**  
 指定如果键入完成列表中某条目的所有字符后按 Enter，则自动创建新行并且光标移动到新行。  
  
 例如，如果键入 `else` 后按 Enter，则编辑器中显示以下内容：  
  
 `else`  
  
 `|`（光标位置）  
  
 但是，如果仅键入 `el`，然后按 Enter，则编辑器中显示以下内容：  
  
 `else|`（光标位置）  
  
## <a name="intellisense-member-selection"></a>IntelliSense 成员选择  
 **预先选择最近使用过的成员**  
 选择此选项后，在集成开发环境 (IDE) 中当前会话期间，IntelliSense 将预先选择 会你最近在弹出“列表成员”框中选择的成员自动完成对象名称。 在 IDE 中的每个会话之间，最近使用过的成员的历史记录将被清除。 有关详细信息，请参阅[用于最近使用过的成员的 IntelliSense](../../ide/visual-csharp-intellisense.md#most-recently-used-members)  
  
## <a name="see-also"></a>另请参阅  
 [“选项”对话框 ->“环境”->“常规”](../../ide/reference/general-environment-options-dialog-box.md)   
 [XML 文档注释](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)   
 [使用 IntelliSense](../../ide/using-intellisense.md)