---
title: "在代码编辑器中编写代码 | Microsoft Docs"
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.texteditor
dev_langs:
- JScript
- VB
- CSharp
helpviewer_keywords:
- code editor, word wrap
- outlining
- code, editing
- squiggles
- code editor, outlining
- code editor, error and warning markers
- word wrap
- code editor, syntax coloring
- code editor, go to definition
- diff
- code editor [Visual Studio]
- code editor, diff
- error and warning markers
- code editor, navigation bar
- code editor, customizing
- comment selection
- code editor, tabify
- brace matching
- code editor, line numbers
- printing
- code editor, brace matching
- code editor, squiggles
- code editor, features
- line numbers
- go to definition
- syntax coloring
- code editor, go to
- code editor, comparing files
- code editor, zoom
- code editor
- code files
- go to line
- tabify
- zoom
- go to
- line break characters
- code editor, virtual space
- code editor, change tracking
- code editor, comment selection
- code editor, printing
- virtual space
- code editor, line break characters
- code editor, go to line
- code
ms.assetid: cb53ab9a-5b76-4759-b9e8-7bf32298ecbe
caps.latest.revision: 44
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 7b3cc733a1a808f60a27332024bcfff1dd9e670b
ms.contentlocale: zh-cn
ms.lasthandoff: 05/13/2017

---
# <a name="write-code-in-the-code-editor"></a>在代码编辑器中编写代码
Visual Studio 编辑器提供了许多功能，可方便你更加轻松地编写和管理代码和文本。 可通过使用大纲显示来展开和折叠不同的代码块。 可通过使用 IntelliSense、“对象浏览器” 以及调用层次结构，了解有关正在使用的代码的详细信息。 可使用“转到”、“转到定义”和“查找所有引用”等功能查找代码。 可以将插入代码块和代码片段，并且可以通过“使用时生成” 等功能生成代码。 如果之前从未用过 Visual Studio 编辑器，请参阅[编辑代码](https://www.visualstudio.com/features/ide-vs)进行快速概览。  

 可以使用多种不同的方式查看自己的代码。 若要查看解决方案的类视图，可以打开“类视图”窗口或展开“解决方案资源管理器”中类文件下的节点。

 可以搜索和替换单个或多个文件的文本。 有关详细信息，请参阅[查找和替换文本](../ide/finding-and-replacing-text.md)。 可以使用正则表达式来查找和替换文本。 有关详细信息，请参阅[在 Visual Studio 中使用正则表达式](../ide/using-regular-expressions-in-visual-studio.md)。  

 不同的 Visual Studio 语言提供不同的功能集，在某些情况下，同样的功能在不同语言中的行为也会有所不同。 功能说明中已指出多数差异，但如需有关详细信息，可以参阅特定 Visual Studio 语言相关章节。  

> [!IMPORTANT]
>  正在使用的 Visual Studio 版本和设置可能会影响 IDE 中的功能。 它们可能与本主题中介绍的功能有所不同。  

## <a name="editor-features"></a>编辑器功能  

|||  
|-|-|  
|语法着色|用不同颜色对代码和标记文件中某些语法元素着色，从而将它们区分开来。 例如，关键字（如 C# 中的 `using` 和 Visual Basic 中的 `Imports` ）用一种颜色，类型（如 `Console` 和 `Uri`用另一种颜色。 也为其他语法元素（如字符串文本和注释）着色。 C++ 使用颜色来区分类型、枚举、宏以及其他标记。<br /><br /> 可以看到每种类型的默认颜色，并且可以更改可从“工具”菜单打开的 [Fonts and Colors, Environment, Options Dialog Box](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)中任意特定语法元素的颜色  。|  
|错误和警告标记|添加代码和生成解决方案时，可能会看到 (a) 不同颜色的波浪下划线（称为波形曲线）或者 (b) 灯泡显示在你的代码中。 红色波浪线表示语法错误，蓝色表示编译器错误，绿色表示警告，而紫色表示其他类型的错误。 [灯泡](../ide/perform-quick-actions-with-light-bulbs.md) 建议了问题的修补程序，并简化修补程序的应用。<br /><br /> 可在“工具/选项/环境/字体和颜色”  对话框中看到每种错误和警告曲线的默认颜色。 查找“语法错误” 、“编译器错误” 、“警告” 和“其他错误” 。|  
|括号匹配|插入点放置在代码文件中的左大括号上时，将突出显示左大括号和右大括号。 此功能可为你提供有关错放或丢失大括号的即时反馈。 可以使用“自动突出显示分隔符”  设置来启用或禁用大括号匹配（“工具/选项/文本编辑器”）。 可以在“字体和颜色”  设置中更改突出显示颜色（“工具/选项/环境”）。 查找“大括号匹配（突出显示）”  或“大括号匹配（方括号）” 。|  
|结构可视化工具|在代码文件中，成对的大括号用虚线相连，方便你更加轻松地辨别左大括号和右大括号对。 这样一来，你可以在代码库中更快速地找到代码。 可以使用“工具”/“选项”/“文本编辑器”/“常规”页上“显示”部分中的“显示结构准则”启用或禁用这些代码行。|
|行号|可在代码窗口的左边距中显示行号。 默认情况下不显示行号。 可在“文本编辑器的所有语言”  设置中启用此选项（“工具/选项/文本编辑器/所有语言”）。 可以通过更改各编程语言的设置来显示其行号（“工具/选项/文本编辑器/\<语言>”）。 对于要打印的行号，则必须在“打印”  对话框中选择“包括行号”。|  
|更改跟踪|左边距的颜色使你能够跟踪在文件中所做的更改。 打开文件后所做的未保存的更改将由左边距上的黄色栏（称为选定内容的边距）表示。 保存更改后（但在关闭文件前），该栏将变为绿色。 如果在保存文件后撤消更改，则该栏将变为橙色。 若要禁用和启用此功能，请在“文本编辑器”  设置中更改“跟踪更改”  选项（“工具/选项/文本编辑器”）。|  
|选择代码和文本|可以在标准的连续流模式或框模式中选择文本，你将在其中选择一个矩形部分的文本而非一组文本行。 若要在框模式中进行选择，请在将鼠标拖到选定内容上时按下 Alt 键（或按 Alt + Shift + \<箭头键>）。 选定内容包括由所选范围中第一个字符和最后一个字符所定义的矩形内的所有字符。 键入或粘贴到所选区域内的任何内容均将在每行中的相同点插入。|  
|缩放|可以通过按住 CTRL 键并移动鼠标滚轮（或按 CTRL + SHIFT + . 进行放大，CTRL + SHIFT + , 进行缩小）在任何代码窗口中进行放大或缩小。 可以使用代码窗口左下角的“缩放”框设置特定的缩放百分比。 缩放功能不适用于工具窗口。|  
|虚空格|默认情况下，Visual Studio 编辑器中的行在最后一个字符后结束，从而行尾的向右键会将光标移到下一行的开头。 在某些其他编辑器中，行并不在最后一个字符后结束，你可以将光标放置在行上的任意位置。 可以在“工具/选项/文本编辑器/所有语言”  设置中启用编辑器中的虚空格。 请注意，可以启用“虚空格”  或“自动换行” 之一，但不能同时启用这两者。|  
|打印|打印文件时，可以使用“打印”  对话框中的选项来包括行号或隐藏折叠的代码区域。 在“页面设置”  对话框中，还可以通过选择“页面页眉” 来打印完整路径及文件名。<br /><br /> 可以在“工具/选项/环境/字体和颜色”  对话框中设置颜色打印选项。 在“显示以下对象的设置”  列表中选择“打印机”  ，以自定义彩色打印。 可以为打印文件而非编辑文件指定不同的颜色。|  
|全局撤消和重做|“编辑”  菜单上的“撤消上次全局操作”  和“重做上一全局操作”  命令可撤消或重做影响多个文件的全局操作。 全局操作包括重命名类或命名空间、在解决方案中执行查找和替换操作、重构数据库或更改多个文件的任何其他操作。 可对当前 Visual Studio 会话中的操作应用全局撤消和重做命令（甚至在关闭应用操作的解决方案之后）。|  

## <a name="advanced-editing-features"></a>高级编辑功能  
 可以在“编辑/高级”  子菜单中找到许多高级功能。 并非所有这些功能都可用于所有类型的代码文件。  

|||  
|-|-|  
|设置文档的格式|设置适当的代码行缩进，并移动大括号以分隔文档中的行。|  
|设置选定内容的格式|设置适当的代码行缩进，并移动大括号以分隔选定内容中的行。|  
|将选定行中的空格替换为制表符|在适当的位置将前导空格更改为选项卡。|  
|将选定行中的制表符替换为空格|将前导制表符更改为空格。 如果要将文件中的所有空格都转换为制表符（或将所有制表符转换为空格），可以使用 `Edit.ConvertSpacesToTabs` 和 `Edit.ConvertTabsToSpaces` 命令。 这些命令不会出现在 Visual Studio 菜单中，但可以从快速访问窗口或命令窗口中进行调用。|  
|转换为大写|将选定内容中的所有字符更改为大写；如果未选择任何内容，则将插入点处的字符更改为大写。|  
|转换为小写|将选定内容中的所有字符更改为小写；如果未选择任何内容，则将插入点处的字符更改为小写。|  
|将选定行上移|将选定行上移一行。 快捷键：ALT + 向上箭头。|
|将选定行下移|将选定行下移一行。 快捷键：ALT + 向下箭头。|
|验证文档|验证 JScript 代码文件。|  
|删除水平空白|删除当前行末尾的制表符或空格。|  
|查看空白|将空格显示为上移的点，将制表符显示为箭头。 文件末尾将显示为矩形标志符号。 如果已选择“工具/选项/文本编辑器/所有语言/自动换行/显示可见的自动换行标志符号”  ，则也将显示该标志符号。|  
|自动换行|使文档中的所有行在代码窗口中均可见。 可以在“文本编辑器的所有语言”设置中禁用和启用自动换行（“工具/选项/文本编辑器/所有语言”）。|  
|取消注释选定内容|向选定内容或当前行添加注释字符。|  
|注释选定内容|从选定内容或当前行删除注释字符。|  
|增加行缩进|向所选行或当前行添加一个制表符（或等效空格）。|  
|减少行缩进|从所选行或当前行删除一个制表符（或等效空格）。|  
|选择标记|在包含标记（如 XML 或 HTML）的文档中选择标记。|  
|选择标记内容|在包含标记（如 XML 或 HTML）的文档中选择内容。|  

## <a name="navigate-and-find-code"></a>导航和查找代码  
可以使用多种不同的方式在文档中移动。 除标准操作外，还可以使用工具栏上的“向后导航”  （CTRL + 减号）和“向前导航” （CTRL + SHIFT + 减号）按钮，将插入点移到先前位置，或返回到活动文档中更新的位置。 这些按钮保留插入点的最后 20 个位置。

![向前和向后导航按钮](../ide/media/vs2017_nav_buttons.png)

代码编辑器中的结构可视化工具功能可显示*结构参考线*，即指明代码库中成对大括号的垂直虚线。 这样一来，你可以更加轻松地判断逻辑块的开始和结束位置。

![结构可视化工具](../ide/media/vside_structure_visualizer.png)

若要禁用结构参考线，请依次转到“工具”、“选项”、“文本编辑器”和“常规”，然后取消选中“显示结构参考线”框。

也可以在代码窗口中使用增强型滚动条来获取代码的鸟瞰视图。 在映射模式下，当游标在滚动条上上下移动时可查看代码的预览。有关详细信息，请参阅 [How to: Track Your Code by Customizing the Scrollbar](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)。  

以下命令是特定于代码的导航方法：  

|||  
|-|-|  
|查找所有引用|（上下文菜单或 SHIFT + F12）：查找对解决方案中选定元素的所有引用。|  
|转到|包含以下命令：“转到行”(CTRL + G)：移到活动文档中的指定行号。 “转到所有”(CTRL + T)：移到指定的行、类型、文件、成员或符号。 “转到文件”（CTRL + 1、CTRL + F）：移到解决方案中的指定文件。 “转到类型”（CTRL + 1、CTRL + T）：移到解决方案中的指定类型。 “转到成员”（CTRL + 1、CTRL + M）：移到解决方案中的指定成员。 “转到符号”（CTRL + 1、CTRL + S）：移到解决方案中的指定符号。 有关这些命令的详细信息，请参阅本主题后面的“使用‘转到’命令查找代码”部分。|  
|转到定义|（上下文菜单或 F12）：查找选定元素的定义。|  
|转到实现|（上下文菜单或 CTRL + F12）：查找代码中实现选定元素的位置。|
|查看定义|（上下文菜单或 ALT + F12）：查找选定元素的定义，并将其显示在代码编辑器的窗口中。 有关详细信息，请参阅[如何：使用查看定义 (Alt+F12) 查看和编辑代码](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)。|  
|下一个方法，上一个方法|（“编辑/下一个方法，上一个方法”）在 Visual Basic 代码文件中，使用这些命令将插入点移动到不同的方法。|  
|引用突出显示|单击源代码中的符号时，将在文档中突出显示该符号的所有实例。 突出显示的符号可能包括声明和引用，以及许多其他“查找所有引用”  将返回的符号。 其中包括类、对象、变量、方法和属性的名称。 在 Visual Basic 代码中，也将突出显示许多控件结构的关键字。 若要移至下一个或上一个突出显示的符号，请按 CTRL+SHIFT+向下键或 CTRL+SHIFT+向上键。 可以在“工具/选项/环境/字体和颜色/突出显示的引用” |  
|查找代码相关信息|在代码编辑器中使用 CodeLens 时，可以找到有关特定代码的信息，如更改和更改者、引用、Bug、工作项、代码评审和单元测试状态。 将 Visual Studio Enterprise 与 Team Foundation Server 一起使用时，CodeLens 的工作原理类似于警告显示。 请参阅[查找代码更改和其他历史记录](../ide/find-code-changes-and-other-history-with-codelens.md)。|
|查看调用层次结构|（上下文菜单或 CTRL + K、CTRL + T）。|  

 也可以使用“导航栏”（代码窗口顶部的下拉框），在代码库中查找代码。 选择类型或成员即可直接转到。 在 Visual Basic、C# 或 C++ 代码库中编辑代码时，可以看到导航栏。

 ![代码导航栏](../ide/media/vside_navigation_bar.png)

 若要隐藏导航栏，请在“文本编辑器”的“所有语言”设置中更改“导航栏”选项（依次选择“工具”、“选项”、“文本编辑器”和所有语言”，也可以单独更改各语言的设置）。 可在下拉框中导航，如下所示：  

-   若要将焦点从代码窗口切换到导航栏，请按快捷组合键 CTRL+F2。  

-   若要将焦点从导航栏返回到代码窗口，请按 ESC 键。  

-   若要在导航栏上的项之间切换焦点，请按 TAB 键。  

-   若要选择具有焦点的导航栏项并返回 IDE，请按 ENTER 键  

-   若要转到类或类型，请选择左侧下拉列表中的相应名称。  

-   若要直接转到类中的过程，请选择右侧下拉列表中的过程。  

 在分部类中，可能会禁用在当前代码文件之外定义的成员（灰显）。  

## <a name="find-code-using-go-to-commands"></a>使用“转到”命令查找代码
Visual Studio 的“转到”命令可对代码执行重点搜索，有助于在代码文件、文件路径和代码符号中快速找到指定项。 与其他文本搜索（如“查找”或“在文件中查找”）不同，“转到”命令会将搜索范围缩小为实际代码所在的区域，如文件、窗体和代码模块。 例如，在 ASP.NET Web 应用中搜索某个字符串时，如果在整个解决方案中使用“查找”或“在文件中查找”，那么匹配项可能包括代码注解中的字符串实例。 不过，使用“转到”命令，搜索可能会直接定位要查找的函数，而忽略代码注解中的字符串实例。

### <a name="find-code-using-go-to"></a>使用“转到”命令查找代码

1. 在 Visual Studio 中打开解决方案或文件夹。
1. 在主菜单中，依次选择“编辑”和“转到”。 代码编辑器的上方会出现一个小文本框。
1. 在文本框中，输入要查找的代码元素的名称。

    ![“导航到”窗口](../ide/media/vside_navigatetowindow.png "“导航到”窗口")

    键入内容时，结果显示在文本框下的下拉列表中。
1. 若要转到某个元素，请在列表中选择它。


### <a name="filter-your-search"></a>筛选搜索

默认会在所有解决方案项中搜索指定项。 不过，可以在搜索词前面加上特定字符，将代码搜索范围缩小至具体元素类型。 打开“转到”对话框的最简单方法是按 CTRL + T，然后可以将前置字符更改为下面列出的字符之一。 （也可以选择以下快捷键，自动为你添加字符。）

|符号|描述|  
|-|-|
|无|无前置字符。 这会在所有的行、文件、类型、成员和符号中查找指定项。 快捷键：CTRL + T|
|:|转到指定行号。 快捷键：CTRL + G|
|f|转到指定文件名。 快捷键：CTRL + 1、CTRL + F|
|T|转到指定类型。 快捷键：CTRL + 1、CTRL + T|
|m|转到指定成员。 快捷键：CTRL + 1、CTRL + M|
|#|转到指定符号。 快捷键：CTRL + 1、CTRL + S|

例如，若要将搜索范围缩小至仅搜索代码符号，请按 CTRL + T（或 CTRL + ,）打开“转到”对话框，然后在“转到”查询前面添加“#”字符，或在菜单上依次选择“编辑”、“转到”、“转到符号”。 例如，搜索“`# application`”只会显示包含“application”一词的代码符号。

还可以选择“转到”对话框工具栏上的按钮，快速更改搜索筛选器。 筛选器更改按钮位于左侧，而搜索范围更改按钮则位于右侧。

![](../ide/media/vside_navigation_toolbar.png)

如果在代码中使用[驼峰式大小写](https://en.wikipedia.org/wiki/Camel_case)，可以仅输入代码元素名称的大写字母，更快地查找代码元素。 例如，如果代码中有 `CredentialViewModel` 类型，可以选择“类型筛选器”("t")，然后在“转到”对话框中仅输入名称的大写字母 (`CVM`) 来缩小搜索范围。

![转到窗口 - 使用大写字母进行搜索](../ide/media/vside_capitalsearch.png)

如果代码名称很长，此功能就非常有用。

## <a name="finding-references-in-your-codebase"></a>在代码库中查找引用
若要在整个代码库中查找引用特定代码元素的位置，可以使用“查找所有引用”命令。 若要使用“查找所有引用”，请在要查找其引用的元素的上下文（右键单击）菜单上选择此命令，或按 SHIFT + F12 键。

结果显示在 **'*{element}*' references** 工具窗口中，其中 *{element}* 是要搜索的项名称。 使用此引用窗口中的工具栏，可以：
- 在下拉列表框中更改搜索范围。 选择仅在已更改的文档中进行查找，一直到查找完整个解决方案。
- 通过选择“复制”按钮，复制引用的选定项。
- 通过选择按钮转到列表中的下一或上一位置，或按 F8 和 SHIFT + F8 键。
- 选择“清除所有筛选器”按钮，清除返回结果上的所有筛选器。
- 选择“分组依据:”下拉列表框中的设置，更改返回项的分组方式。
- 选择“保留结果”按钮，保留当前的搜索结果窗口。
- 在“搜索‘查找所有引用’”文本框中输入文本，在搜索结果中搜索字符串。

还可以将鼠标悬停在任一搜索结果之上，从而预览返回项。

![“查找所有引用”工具窗口](../ide/media/vside_findallreferences.png)

若要保留搜索结果，请选择“保留结果”按钮。 选择此按钮后，当前的搜索结果会继续保留在此窗口中，而新的搜索结果则会显示在新的工具窗口中。

### <a name="navigate-to-references"></a>转到引用
在“查找所有引用”对话框中，可以使用以下方法转到引用。

- 按 F8 键可以转到下一个引用，按 SHIFT + F8 键可以转到上一个引用。
- 对引用按 ENTER 键，或双击引用在代码中转到此引用。
- 在引用的上下文菜单中，选择“转到上一位置” / “转到下一位置”命令。
- 按向上和向下箭头键（如果已在“选项”对话框中启用的话）。 若要启用此功能，请在菜单上依次选择“工具”、“选项”、“环境”、“选项卡和窗口”和“预览选项卡”，然后选中“允许在预览选项卡中打开新文件”和“在‘查找结果’中预览选定的文件”框。

### <a name="change-reference-groupings"></a>更改引用分组
默认情况下，引用是先按项目进行分组，然后再按定义进行分组。 不过，可以更改工具栏上“分组依据:”下拉列表框中的设置，从而更改此分组顺序。 例如，可以将其从默认设置“先按定义，然后按项目”更改为“先按项目，然后按定义”，也能更改为其他设置。

虽然“定义”和“项目”是默认使用的两个分组，但可以在选定项的上下文菜单中选择“分组”命令，从而添加其他分组。 如果解决方案有许多文件和路径，那么添加其他分组将会很有帮助。

## <a name="customize-the-editor"></a>自定义编辑器  
可以与其他开发者共享 Visual Studio 设置，可以让自己的设置符合某一标准，也可以使用“工具”菜单上的“导入和导出设置向导”命令恢复 Visual Studio 默认设置。 在“导入和导出设置向导”中，可以更改选定常规设置或语言以及项目专属设置。

若要定义新热键或重新定义现有热键，请依次转到“工具”、“选项”、“环境”和“键盘”。 有关热键的详细信息，请参阅[默认键盘快捷键](../ide/default-keyboard-shortcuts-in-visual-studio.md)。  

若要详细了解如何自定义编辑器，请参阅[自定义编辑器](../ide/customizing-the-editor.md)。 若要了解语言专用编辑器选项，请参阅[将 Visual Studio 开发环境用于 C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md) 和[选项、文本编辑器、JavaScript、格式](../ide/reference/options-text-editor-javascript-formatting.md)。

## <a name="see-also"></a>另请参阅  
 [Visual Studio IDE](../ide/visual-studio-ide.md)

