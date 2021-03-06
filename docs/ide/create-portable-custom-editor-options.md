---
title: "使用 EditorConfig 创建可移植的自定义编辑器设置 | Microsoft Docs"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 29
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
ms.technology:
- vs-ide-general
ms.translationtype: Human Translation
ms.sourcegitcommit: 46846db26bee30841e6cb35913d533b512d01ba0
ms.openlocfilehash: f377ada139d9c0e8b01b640cf603cf349dc1c3c3
ms.contentlocale: zh-cn
ms.lasthandoff: 03/27/2017

---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>使用 EditorConfig 创建可移植的自定义编辑器设置
Visual Studio 中的文本编辑器设置适用于给定类型的所有项目。 因此，如果更改 C# 文本编辑器设置，该设置也适用于 Visual Studio 中的所有 C# 项目。 但是，在某些情况下，可能需要使用不同于个人编辑器首选项的约定。 [EditorConfig](http://editorconfig.org/) 文件基于每个项目提供常用的文本编辑器选项，可让你达到此目的。 EditorConfig 设置包含在已添加到代码库的.editorconfig 文件中，取代 Visual Studio 文本编辑器中的全局设置。 这意味着，可以调整每种基本代码，以使用喜欢的文本编辑器设置。 在 Visual Studio 中使用此功能无需任何插件。

## <a name="coding-consistency"></a>编码一致性
EditorConfig 文件中的设置用于维护某种语言一致的编码风格和设置，例如基本代码中的缩进样式、选项卡宽度、行尾字符以及编码等，而无需考虑使用的编辑器或 IDE。 例如，使用 C# 编码时，如果基本代码约定为始终缩进五个空格字符、文档使用 UTF-8 编码，且每一行始终以 CR/LF 结束，则可以配置 .editorconfig 文件达到此效果。

个人项目中使用的编码约定可能不同于团队项目使用的编码约定。 例如，你可能倾向在编码时按 Tab 键添加制表符。 但你的团队可能更倾向使用四个空格字符的缩进，而不是制表符。 EditorConfig 文件让你能对每个方案进行配置，从而解决这一问题。

由于这些设置包含在基本代码的文件中，因此能与基本代码一起移动。 只要在 EditorConfig 兼容的编辑器中打开代码文件，就能实现文本编辑器设置。 有关 EditorConfig 文件的详细信息，请参阅 [EditorConfig.org](http://editorconfig.org/) 网站。 如果编辑大量 .editorconfig 文件，可能会发现 [EditorConfig 语言服务](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig)扩展很有用。

## <a name="override-editorconfig-settings"></a>替代 EditorConfig 设置
如果在文件层次结构中将 .editorconfig 文件添加到文件夹，则其设置将应用于该级别和更低级别的所有适用文件。 若要替代特定项目或基本代码的 EditorConfig 设置，并使用异于顶级 .editorconfig 文件的不同值或替代值，只需将 .editorconfig 文件添加到想要更改的级别即可。

![EditorConfig 层次结构](../ide/media/vside_editorconfig_hierarchy.png)

新的 .editorconfig 文件设置将应用于其所在级别和所有子文件。

## <a name="supported-settings"></a>支持的设置
Visual Studio 中的编辑器支持 EditorConfig 选项核心组的以下值。
- indent_style
- indent_size
- tab_width
- end_of_line
- charset
- 根
- [代码样式约定](../ide/editorconfig-code-style-settings-reference.md)

所有 Visual Studio 支持的语言（XML 除外）均支持 EditorConfig 设置。

## <a name="example"></a>示例
以下示例演示将 .editorconfig 文件添加到项目之前和之后 C# 代码片段的缩进状态。 Visual Studio 文本编辑器“选项”对话框中的“Tab”设置被设置为在代码中按 Tab 键时可生成空格字符。

![文本编辑器 Tab 设置](../ide/media/vside_editorconfig_tabsetting.png)

按预期，在下一行按 Tab 键会使该行首行缩进四个空格字符。

![使用 EditorConfig 之前的代码](../ide/media/vside_editorconfig_before.png)

将以下名为 .editorconfig 的新文件添加到项目。 （`[*.cs]` 设置意味着此更改仅应用于此项目中的 .cs 文件。）

![已将 .editorconfig 文件添加到项目](../ide/media/vside_editorconfig_addconfig.png)

现在，如果按 Tab 键，会获得制表符而非空格。

![使用 Tab 添加制表符](../ide/media/vside_editorconfig_tab.png)

> [!NOTE]
>  将 .editorconfig 文件添加到项目或基本代码不会将现有样式转换为新样式，而仅应用于新添加的行。 如果从项目或基本代码删除 .editorconfig 文件，必须重新加载编辑器设置的代码文件，还原为全局设置。 在 Visual studio 中，.editorconfig 文件中的任何错误都会报告在“错误”窗口。

## <a name="support-editorconfig-for-your-language-service"></a>支持语言服务的 EditorConfig

在大多数情况下，实现 Visual Studio 语言服务时，无需任何其他工作即可支持 EditorConfig 通用属性。 当用户打开文件时，核心编辑器将自动发现并读取 .editorconfig 文件，并设置相应的文本缓冲区和视图选项。 但是，用户编辑或设置文本格式时，某些语言服务将选择使用相应的上下文文本视图选项，而不是对制表符和空格等项使用全局设置。 在这些情况下，必须更新语言服务以支持 EditorConfig 文件。

下表列出了更新语言服务以支持 EditorConfig 文件所需的更改。

| 已弃用的全局语言特定选项 | 上下文选项替换 |
| :------------- | :------------- |
| Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs 或 Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs | !textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId) 或 !textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId) |
| Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize 或 Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize | textBufferOptions.GetOptionValue(DefaultOptions. IndentSizeOptionId) 或 textView.Options.GetOptionValue(DefaultOptions. IndentSizeOptionId) |
| Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize 或 Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize | textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId) 或 textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId) |

# <a name="see-also"></a>另请参阅
[使用 EditorConfig 创建可移植的自定义编辑器设置](create-portable-custom-editor-options.md)
