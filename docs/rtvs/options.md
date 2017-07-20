---
title: "Visual Studio 中的 R 工具选项 | Microsoft Docs"
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
f1_keywords:
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
ms.topic: article
ms.assetid: 554dc602-ecad-4cd0-8e6f-a60bb8a2328f
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
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
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 9b680c73d54c9809e3f4c46dc2841f1f320e4af9
ms.contentlocale: zh-cn
ms.lasthandoff: 05/12/2017

---


# <a name="r-tools-for-visual-studio-options"></a>针对 Visual Studio 的 R 工具选项
 
要访问设置，可使用“R 工具”>“选项”**菜单，也可使用“工具”>“选项”****，然后滚到“R 工具”**进：
 
  ![R 工具的选项对话框](media/options-dialog.png)

以下各节描述此页中提供的各个选项...

> [!Note]
> 通过常规的“工具”>“选项”菜单访问选项时，可能需要选择底部的“显示所有设置”框，才会显示“R 工具”页。

<a name="data-scientist-layout"</a>

还有一个特殊菜单项 “R 工具”>“数据科学设置”，可使用针对数据科学家的需求进行了优化的布局来配置 Visual Studio IDE。 具体而言，这个选项将打开[交互](interactive-repl.md)、[变量资源管理器](variable-explorer.md)和[工作区](workspaces.md)窗口：

![Visual Studio 中的数据科学家窗口布局](media/installation-data-scientist-layout-result.png)

> [!Important]      
> 若稍后要还原到其他 Visual Studio 设置，请先使用“工具”>“导入和导出设置”命令，选择“导出所选环境设置”，然后指定一个文件名。 若要还原这些设置，请使用相同的命令，然后选择“导入所选环境设置”。 如果要更改数据科学家布局，并且想要稍后返回该布局，还可使用相同的命令，而不是直接使用“数据科学设置”命令。

## <a name="debugging"></a>调试

以下选项可控制在[变量资源管理器](variable-explorer.md)和调试器工具窗口中处理值（如监视和局部变量）的方式（请参阅[调试](debugging.md)）。

| 选项 | 默认值 | 描述 | 
| --- | --- | --- |
| 评估活动绑定 | `True` | 如果为 `True`，可确保在检查变量和属性时始终看到最新值。 风险是计算表达式的值可能产生副作用，具体取决于实现方式。 |
| 显示以圆点作为前缀的变量 | `False` | 指定是否显示以 `.` 作为前缀的变量。 |

## <a name="general"></a>常规

| 选项 | 默认值 | 描述 | 
| --- | --- | --- |
| 调查/新闻检查 | `Once a week` | 指定 R 工具检查服务器以查看新闻和调查更新的频率。 | 

## <a name="help"></a>帮助

| 选项 | 默认值 | 描述 | 
| --- | --- | --- |
| F1 Web 浏览器 | `Internal` | 控制使用 Ctrl+F1 搜索术语时帮助的显示方式。 如果设置为 `Internal`，帮助将在 Visual Studio 的工具窗口内呈现。 如果设置为 `External`，帮助将出现在默认的 Web 浏览器中。 | 
| F1 Web 搜索字符串 | `R site:stackoverflow.com` | 控制在编辑器中的术语上按 Ctrl+F1 时，向搜索引擎传递搜索词的方式。 默认情况下，字符串为 `R site:stackoverflow.com`，它将 `R` 追加到搜索词。 `site:stackoverflow.com` 是向搜索引擎发出的指令，告诉搜索引擎将搜索范围限定在 `stackoverflow.com` 域内的页面内。 | 
| R 帮助浏览器 | `Automatic` | 控制使用 Ctrl+F1、`?` 或 `??` 搜索 R 文档时帮助的显示方式。 如果设置为 `Automatic`，帮助将在相应的窗口中呈现。 例如，HTML 帮助将在 Visual Studio 工具窗口中出现，而 PDF 帮助在默认的 PDF 程序中出现。 如果设置为 `External`，帮助将在默认的 Web 浏览器中呈现。 |

## <a name="history"></a>历史记录

| 选项 | 默认值 | 描述 | 
| --- | --- | --- |
| 始终保存历史记录 | `True` | 控制每当关闭项目时，RTVS 是否将命令历史记录写入工作目录中的 `.RHistory` 文件。 请注意，即使在退出前不保存项目，这种情况仍会发生。 |
| 重置搜索筛选器 | `True` | 确定历史记录窗口是否可以筛选命令历史记录，以便只显示子字符串与“R 历史记录”对话框中的筛选器术语匹配的命令。 此设置确定每次运行新命令或切换到新项目时，是否重置历史记录搜索筛选器，这将触发加载其他 `.RHistory` 文件。 使用筛选器集执行命令时，以及想要知道刚运行的命令为何未在历史记录中显示时，使用默认设置 `True` 可最大限度减少意外情况的发生。 |
| 使用多行选择 | `True` | 指定是否可以通过单击在历史记录中选择多行语句。 还可在交互窗口中使用向上键/向下键按语句而不是行进行导航。 |

## <a name="html"></a>HTML

| 选项 | 默认值 | 描述 | 
| --- | --- | --- |
| HTML 页面浏览器 | `External` | 确定在哪个位置呈现 `ggvis` 绘图或 `shiny` 应用程序等内容。 值为 `Internal` 时，在 Visual Studio 的工具窗口中显示 HTML 输出，而值为 `External` 时，在默认浏览器中显示 HTML 输出。 | 

## <a name="logging"></a>日志记录

| 选项 | 默认值 | 描述 | 
| --- | --- | --- |
| 日志事件 | `Normal` | 控制用于 RTVS 诊断的日志记录的详细级别。 使用默认设置 `Normal` 可在 `TEMP` 目录中创建一个日志文件。 如果设置为 `Traffic`，RTVS 将记录所有命令和会话中的响应。 这些日志文件始终都将保存在计算机中，但对诊断 RTVS 中的问题可能十分有用。 |

## <a name="markdown"></a>Markdown

| 选项 | 默认值 | 描述 | 
| --- | --- | --- |
| Markdown 预览浏览器 | `External` | 确定在何处显示 RMarkdown HTML 输出。 使用值 `Internal` 时，在 Visual Studio 的工具窗口中显示 RMarkdown HTML 文档，而使用值 `External` 时，使用默认浏览器显示 RMarkdown HTML。 | 

## <a name="r-engine"></a>R 引擎

| 选项 | 默认值 | 描述 | 
| --- | --- | --- |
| 代码页 | `(OS Default)` | 设置 R 的代码页（区域设置）。默认情况下，使用的是操作系统的基础区域设置。 | 
| CRAN 镜像 | `(Use .Rprofile)` | 设置用于包安装的默认 CRAN 镜像。 使用默认设置 `Use .Rprofile` 时，沿用 `.RProfile` 文件中的 CRAN 镜像设置。 可以通过在下拉列表中选择一个列出的 CRAN 镜像来进行替代。 |
| 工作目录 | 特定于用户的文件夹 | 设置当前工作目录，通常在每次打开项目时设置。 |

## <a name="workspace"></a>工作区

| 选项 | 默认值 | 描述 | 
| --- | --- | --- |
| 在打开项目时加载工作区 | `No` | 如果设置为 `Yes`，可在打开项目后将会话数据从 `.RData` 文件加载到全局环境中。 |
| 提示在重置时保存工作区 | `Yes` | 如果设置为 `No`，在交互窗口中单击“重置”按钮时，不会出现保存工作区的提示。 |
| 在关闭项目时保存工作区 | `No` | 如果设置为 `Yes`，在关闭项目时，全局环境将保存到 `.RData` 文件中。 |
| 切换工作区前显示确认对话框 | `Yes` | 如果设置为 `No`，在不同工作区之间切换时，不会出现用户确认提示。 请参阅[在工作区之间切换](workspaces.md#switching-between-workspaces) |
 
