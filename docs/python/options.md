---
title: "Visual Studio 中的 Python 选项 | Microsoft Docs"
ms.custom: 
ms.date: 7/13/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c714867-7a64-4b1e-aca8-09d956192279
f1_keywords:
- VS.ToolsOptionsPages.Python_Tools
- VS.ToolsOptionsPages.Python_Tools.General
- VS.ToolsOptionsPages.Python_Tools.Debugging
- VS.ToolsOptionsPages.Python_Tools.Interactive_Windows
- VS.ToolsOptionsPages.Text_Editor.Python.Advanced
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: a71d076e85e1e7ae070014e83186c0011ca9e58f
ms.contentlocale: zh-cn
ms.lasthandoff: 07/18/2017

---

# <a name="options-for-python-in-visual-studio"></a>Visual Studio 中的 Python 选项

若要查看 Python 选项，请使用“工具”>“选项”菜单命令，确保选择“显示所有设置”，然后导航到“Python 工具”：

![Python“选项”对话框，“常规”选项卡](media/options-general.png)

“文本编辑器”>“Python”>“高级”选项卡上还设有其它特定于 Python 的选项。

以下各部分提供对这些特定选项的说明：

- [常规选项](#general-options)
- [调试选项](#debugging-options)
- [交互窗口选项](#interactive-windows-options)
- [高级 Python 编辑器选项](#advanced-python-editor-options)

## <a name="general-options"></a>常规选项

| 选项 | 默认 | 描述 |
| --- | --- | --- |
| 在创建虚拟环境时显示输出窗口| On | 清除该选项可避免显示输出窗口。 |
| 在安装或删除包时显示输出窗口 | On |  清除该选项可避免显示输出窗口。 |
| 始终以管理员身份运行 pip | Off | 始终为所有环境提升 `pip install` 操作。 安装包时，如果环境位于文件系统（如 `c:\Program Files`）的保护区域内，Visual Studio 将提示需要管理员权限。 出现该提示时，可选择始终仅为此环境提升 `pip install`。 请参阅 [Python 环境 - pip 选项卡](python-environments.md#pip-tab)。 |
| 初次使用时自动生成完成 DB | On | 要使 [IntelliSense 完成](code-editing.md#intellisense)可用于库，Visual Studio 必须为该库生成完成数据库。 安装库后，将在后台生成数据库，但有可能在开始编写代码时此过程还未完成。 选择此选项后，在编写使用某个库的代码时，Visual Studio 会优先完成此库的数据库。 |
| 忽略系统级 PYTHONPATH 变量 | On | 默认情况下会忽略 PYTHONPATH，因为 Visual Studio 提供了一种更直接的方式来指定环境和项目中的搜索路径。 有关详细信息，请参阅 [Python 环境 - 搜索路径](python-environments.md#search-paths)。 |
| 添加链接文件时更新搜索路径 | On | 如果设置此选项，将一个[链接文件](python-projects.md#linked-files)添加到项目会更新[搜索路径](python-environments.md#search-paths)，以便 IntelliSense 能在其完成数据库中包含链接文件的文件夹的内容。 清除此选项将从完成数据库中排除此类内容。 |
| 在找不到导入模块时发出警告 | On | 当知道导入模块当前不可用但不会影响代码操作时，清除此选项可禁止发出警告。 |
| 将缩进不一致报告为 | 警告 | 由于 Python 解释器严重依赖于正确的缩进来确定作用域，因此默认情况下，Visual Studio 将在检测到可能指示编码错误的缩进不一致时发出警告。 设置为“错误”可提升严格度，这样会导致出现这些情况时退出程序。 若要完全禁用此行为，请选择“不”。 |
| 检查调查/新闻 | 每周一次 | 设置频率，允许 Visual Studio 以此频率打开窗口，此窗口包含一个网页，其中含有 Python 相关的调查和新闻条目（如果有）。 选项包括“从不”、“每天一次”、“每周一次”和“每月一次”。 |
| 重置所有永久隐藏的对话框（按钮） | 无 | 各对话框提供“不再显示”等选项。 使用此按钮可清除这些选项并重新显示对话框。 |

![Python“选项”对话框，“常规”选项卡](media/options-general.png)

## <a name="debugging-options"></a>调试选项

| 选项 | 默认 | 描述 |
| --- | --- | --- |
| 当存在错误时，在运行前发出提示 | On | 如果设置此选项，系统会提示是否确定要运行包含错误的代码。 清除此选项将禁用警告。 |
| 在进程异常退出时等待输入<br/><br/>在进程正常退出时等待输入 | On（两者皆是） | 通过 Visual Studio 启动的 Python 程序在其自己的控制台窗口中运行。 默认情况下，无论程序如何退出，窗口都会等待用户按键才会关闭。 若要删除提示并自动关闭窗口，请清除其中任一选项或全部清除。 |
| 让程序输出显示在“调试输出”窗口 | On | 同时在一个单独的控制台窗口和 Visual Studio 输出窗口中显示程序输出。 清除此选项可仅在单独控制台窗口中显示输出。 |
| 在出现 SystemExit 异常（退出代码为 0）时中断 | Off | 如果设置此选项，将在出现此异常时停止调试器。 清除后，调试器将退出，但不会中断。 |
| 启用调试 Python 标准库 | Off | 可支持在调试时逐步执行标准库源代码，但会增加调试器启动的时间。|

![Python“选项”对话框，“调试”选项卡](media/options-debugging.png)

## <a name="interactive-windows-options"></a>交互窗口选项

| 选项 | 默认 | 描述 |
| --- | --- | --- |
| 脚本 | 无 | 指定启动脚本的常规文件夹，将其应用于所有环境的交互窗口。 请参阅[启动脚本](python-environments.md#startup-scripts)。 但请注意，此功能当前无效。 |
| 可使用向上/向下箭头浏览历史记录 | On | 使用箭头键在交互窗口中浏览历史记录。 清除此设置可改为使用箭头键在交互窗口的输出中浏览。 |
| 完成模式 | 仅评估表达式而无需调用函数 | 要确定交互窗口中表达式上的可用成员，可能需要评估当前未完成的表达式，这可能带来负作用或导致多次调用函数。 “仅评估表达式而无需调用函数”是默认设置，此设置可排除可能调用函数的表达式，并对其他表达式进行评估。 例如，会评估 `a.b`，但不会评估 `a().b`。  “永不评估表达式”仅使用常规 IntelliSense 引擎获取建议，可避免所有副作用。 “评估所有表达式”会评估完整的表达式以获取建议，不考虑是否存在副作用。 |
| 隐藏静态分析建议 | Off | 如果设置此选项，将仅显示通过评估表达式获取的建议。 如果与完成模式“永不评估表达式”结合使用，交互窗口中将不会显示任何有用的完成。 |

![Python“选项”对话框，“交互窗口”选项卡](media/options-interactive-windows.png)

## <a name="advanced-python-editor-options"></a>高级 Python 编辑器选项

### <a name="completion-results"></a>完成结果

| 选项 | 默认 | 描述 |
| --- | --- | --- |
| 成员完成会显示成员的交集 | Off | 如果设置此选项，将仅显示所有可能类型支持的完成。 |
| 基于搜索字符串筛选列表 | On | 在键入时，对完成建议应用筛选（默认选中）。 |
| 自动显示所有标识符的完成 | On | 清除此选项将同时在编辑器和交互窗口中禁用完成。 |

### <a name="selection-in-completion-list"></a>完成列表中的选定内容

| 选项 | 默认 | 描述 |
| --- | --- | --- |
| 通过键入以下字符提交 | {}[]().,:;+-*/%&&#124;^~=<>#@\ | 这些字符通常位于可能是从完成列表中选取的标识符后面，因此只需键入字符即可轻松提交完成。 可根据需要在列表中删除或添加特定字符。  |
| 按 Enter 提交当前完成 | On | 如果设置此选项，按 Enter 键将选择并应用当前选择的完成（和上面的字符一样）（但由于没有针对 Enter 的字符，因此它无法直接进入该列表！）。 |
| 在完整键入的字末尾按 Enter 添加新行 | Off | 默认情况下，如果键入完成弹出窗口中显示的完整字词，然后按 Enter，则会提交该完成。 通过设置此选项，可在键入完标识符后有效提交完成，然后按 Enter 键即可插入新行。 |

### <a name="miscellaneous-options"></a>“杂项”选项

| 选项 | 默认 | 描述 |
| --- | --- | --- |
| 打开文件时进入大纲模式 | On | 打开 Python 代码文件时，自动在编辑器中打开 Visual Studio 的大纲显示功能。 |
| 粘贴已删除的 REPL 提示符 | On | 删除粘贴文本中的 >>> 和 ...，可从交互窗口向编辑器轻松传输代码。 可根据需要清除此选项，以保留从其他源粘贴的字符。 |
| 基于类型为名称着色 | On | 在 Python 代码中启用语法着色。 |

![Python 编辑器“选项”对话框，“高级”选项卡](media/options-editor-advanced.png)
