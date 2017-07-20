---
title: "针对 Visual Studio 的 R 工具 | Microsoft Docs"
ms.custom: 
ms.date: 6/29/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: hero-article
ms.assetid: 11324501-ceb6-47a2-ae13-e9e992d3603e
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: 80a10c710aac8413bd59b53bb61de7a982c09952
ms.contentlocale: zh-cn
ms.lasthandoff: 07/12/2017

---

# 在 Visual Studio 中使用 R
<a id="working-with-r-in-visual-studio" class="xliff"></a>

R 是用于统计计算和图形的高度可扩展语言和环境。 它是使用 GNU 通用公共许可证免费分发的工具，提供强大的社区支持，并因能够生成发布质量的绘图（包括数学符号和公式）而闻名。 若要了解详细信息，请参阅 [r-project.org](https://www.r-project.org/about.html) 和 [R 简介](https://cran.r-project.org/doc/manuals/r-release/R-intro.html)。

针对 Visual Studio 的 R 工具 (RTVS) 是使用 MIT 许可证发布的[开放源代码](https://github.com/microsoft/RTVS)插件，适用于 Visual Studio 2017 和 Visual Studio 2015 Update 3（或更高版本）。 （还有一个链接到 R 解释器二进制文件的开放源代码组件 [RHost](https://github.com/microsoft/R-Host)，它是使用 GNU 公共许可证 V2 进行发布。）

若要在 Visual Studio 中使用 R，请执行以下操作：

- [安装 R 工具](installation.md)。
- 请按照[入门](getting-started-with-r.md)指南、[示例](getting-started-samples.md)和[获取帮助](getting-started-help.md)主题操作。

然后，单击该链接，详细了解与 R 相关的功能，以及 Visual Studio 本身的常规功能。

| 功能 | 说明 | Visual Studio 常规文档 | 
| --- | --- | --- |
| [Visual Studio 项目系统](projects.md) | 利用方便使用的结构整理和管理相关文件，并利用实用项目模板，如 R 代码、R 文档、R Markdown、SQL 查询和存储过程。 此外，还可以使用[程序包管理器](package-manager.md)和 [SQL Server 集成](sql-server.md)。  | [Visual Studio 中的解决方案和项目](../ide/solutions-and-projects-in-visual-studio.md) |
| [工作区](workspaces.md) | RTVS 可以绑定到本地和远程工作区，以便使用较小的数据集在本地开发 R 代码，然后在基于云且功能更强大的计算机上使用较大的数据集运行此代码。 | 无 |
| [R 工具选项](options.md) | 控制 RTVS 的各个方面。 | [“选项”对话框](../ide/reference/options-dialog-box-visual-studio.md) |
| [丰富编辑、IntelliSense 和代码片段](code-editing.md) | 包括语法着色、跨所有代码和库的[IntelliSense](code-intellisense.md)、代码格式设置、签名帮助、转到定义、查找所有引用和[代码片段](code-snippets.md)等。 | [在代码和文本编辑器中编写代码](../ide/writing-code-in-the-code-and-text-editor.md) |
| [R Markdown](rmarkdown.md) | R Markdown 文档可帮助你共享数据结果，其中 Markdown 代码块包含集成的 R 代码。 | 无 |
| [交互窗口](interactive-repl.md) | 提供 R 的完整 REPL 体验，以便你可以在交互窗口内轻松运行源文件中的代码。 | 无 |
| [可视化数据](visualizing-data.md) | 绘图是 R 体验不可或缺的一部分，RTVS 支持使用多个独立绘图窗口（每个窗口均有各自的历史记录）和跨窗口移动绘图功能。 可以将绘图保存为位图和 PDF 文件，也可以将绘图以位图或元文件的形式复制到剪贴板中。  | 无 |
| [变量资源管理器](variable-explorer.md) | 在全局或包特定范围中检查变量，同时还允许你查看可排序的表，并将其导出为 CSV 格式。 | 无 |
| [功能完备的调试](debugging.md) | 包括与交互窗口的集成。 | [在 Visual Studio 中进行调试](../debugger/debugging-in-visual-studio.md) |

下面的视频也简要概览了 R 工具功能（5 分 48 秒）：

> [!VIDEO https://www.youtube.com/embed/RcSDEfMgUvU]

## 常见问题
<a id="frequently-asked-questions" class="xliff"></a>

**问：RTVS 能否用于 Visual Studio Express 版本？**

答： 不是。

**问：哪些 R 解释器可用于 RTVS？**

答： [CRAN R](https://cran.r-project.org/)、[Microsoft R Client 和 Microsoft R Server](https://msdn.microsoft.com/microsoft-r/)

**问：从哪里可以下载这些解释器？**

答： 请参阅[安装](installation.md)。

**问：我能否将 Visual Studio 插件与 RTVS 结合使用？**

答： 当然可以。 实际上，用户常常将下面的一些插件与 R 结合使用。

- [适用于 vim 键绑定的 VsVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [Github](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [提供实时预览的 Markdown Editor](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

请访问 [Visual Studio Marketplace](https://marketplace.visualstudio.com/)，了解详细信息。

**问：由于 RTVS 包含在 Visual Studio 中，这是否意味着可以将 R 轻松用于 C#、C++ 和其他 Microsoft 语言？**

答： 不是。 RTVS 是使用标准本机 R 解释器的 R 代码开发工具。 当前不支持 R 和其他语言之间的互操作。

**问：虽然缺少功能 X，但 RStudio 有！**

答： 经过多年开发，RStudio 已成为适用于 R 的成熟优质 IDE。 RTVS 旨在囊括你取得成功所需的全部关键功能。 请参与 [RTVS 调查](https://www.surveymonkey.com/r/RTVS1)，帮助我们确定未来工作的优先次序。

**问：能否在 OS X 或 Linux 上使用 RTVS？**

答： 不能，RTVS 是在 Visual Studio 的基础之上生成，这是仅限 Windows 的实现。 不过，Microsoft 正在调查生成一组基于 [Visual Studio Code](https://code.visualstudio.com/)（受欢迎的 Microsoft 跨平台编辑器）的新工具。

**问：我能否参与 RTVS 发布？**

答： 当然可以！ 源代码位于 [Github](https://github.com/microsoft/RTVS) 上。 请使用问题跟踪程序来提交 bug，并对已发布的文件发表评论。

也欢迎你参与此文档的编写 &mdash; 只需选择任意页面右上角的“编辑”命令。 同样欢迎在任意页面的底部对文档发表评论。

**问：RTVS 能否用于我的源代码管理系统？**

答： 能，可以使用 Visual Studio 中集成的任何源代码管理系统。

**问：RTVS 能否使用非英语区域设置？**

答： RTVS 1.0 版仅可使用英语。 1.1 版将本地化成 Visual Studio 本身使用的一组相同语言。 在此期间，使用[适用于 Visual Studio 2015 的英语语言包](https://www.microsoft.com/download/details.aspx?id=48157)；或在 Visual Studio 2017 中，运行安装程序，并选择“语言包”选项卡中的“英语”。

![Visual Studio 2017 的“区域设置”](media/FAQ-international-settings.png)

**问：RTVS 能否用于 32 位版本的 R？**

答： 不能，RTVS 仅支持在 64 位版本的 Windows 上运行 64 位版本的 R。

**问：虽然我确实很喜欢当前的 Visual Studio 设置，但我想要尝试新的数据科学设置。我该怎么办？**

答： 请使用“工具 > 导入和导出设置...”，保存当前的 Visual Studio 设置，然后切换到数据科学设置。 若要还原已保存的设置，请再次使用“导入和导出设置...”命令。

**问：建议用于 RTVS 项目的 `.gitignore` 设置是什么？**

答： Github 维护推荐 `.gitignore` 文件的主存储库。 请访问 [R .gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)

**问：我能否在网络共享上存储我的 Visual Studio 项目？**

答： 否，Visual Studio 不支持从网络共享中加载项目。

## 向我们发送反馈！
<a id="send-us-your-feedback" class="xliff"></a>

1. Github 问题：联系 RTVS 团队的最佳方式是[在 GitHub 中上报问题](https://github.com/Microsoft/RTVS/issues)，或使用“R 工具 > 反馈”菜单。

1. 发送笑脸/哭脸：使用“R 工具 > 反馈”菜单，可以快速发送反馈，并附加 RTVS 日志文件，以帮助我们诊断你遇到的问题。 （如果要单独发送，请将日志写入 `%temp%/RTVSlogs.zip`。）如果已使用“帮助 > 反馈 > 设置”菜单命令或在安装期间选择禁用了 Visual Studio 遥测，日志记录也会被禁用。

1. 电子邮件：可以直接向团队发送反馈，地址是 rtvsuserfeedback@microsoft.com。

