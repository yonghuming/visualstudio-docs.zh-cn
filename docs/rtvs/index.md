---
title: "针对 Visual Studio 的 R 工具 | Microsoft Docs"
ms.custom: 
ms.date: 11/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: hero-article
ms.assetid: 11324501-ceb6-47a2-ae13-e9e992d3603e
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 2640607b4b4cd817790048e4e1d497f42ed83a08
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2017
---
# <a name="working-with-r-in-visual-studio"></a>在 Visual Studio 中使用 R

R 是用于统计计算和图形的高度可扩展语言和环境。 它是使用 GNU 通用公共许可证免费分发的工具，提供强大的社区支持，并因能够生成发布质量的绘图（包括数学符号和公式）而闻名。 若要了解详细信息，请参阅 [r-project.org](https://www.r-project.org/about.html) 和 [R 简介](https://cran.r-project.org/doc/manuals/r-release/R-intro.html)。

针对 Visual Studio 的 R 工具 (RTVS) 是使用 MIT 许可证发布的[开放源代码](https://github.com/microsoft/RTVS)插件，适用于 Visual Studio 2017 和 Visual Studio 2015 Update 3（或更高版本）。 （还有一个链接到 R 解释器二进制文件的开放源代码组件 [RHost](https://github.com/microsoft/R-Host)，它是使用 GNU 公共许可证 V2 进行发布。）

> [!Note]
> RTVS 目前仅在 Windows 上的 Visual Studio 中受支持，在 Visual Studio for Mac 中不受支持。

若要在 Visual Studio 中使用 R，请执行以下操作：

- [安装 R 工具](installation.md)。
- 请按照[入门](getting-started-with-r.md)指南、[示例](getting-started-samples.md)和[获取帮助](getting-started-help.md)主题操作。

然后，单击下面的链接，详细了解与 R 相关的功能，以及 Visual Studio 本身的常规功能。

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

另请参阅[常见问题](faq.md)。

下面的视频也简要概览了 R 工具功能（5 分 48 秒）：

> [!VIDEO https://www.youtube.com/embed/RcSDEfMgUvU]

## <a name="send-us-your-feedback"></a>向我们发送反馈！

1. Github 问题：联系 RTVS 团队的最佳方式是[在 GitHub 中上报问题](https://github.com/Microsoft/RTVS/issues)，或使用“R 工具 > 反馈”菜单。

1. 发送笑脸/哭脸：使用“R 工具 > 反馈”菜单，可以快速发送反馈，并附加 RTVS 日志文件，以帮助我们诊断你遇到的问题。 （如果要单独发送，请将日志写入 `%temp%/RTVSlogs.zip`。）如果已使用“帮助 > 反馈 > 设置”菜单命令或在安装期间选择禁用了 Visual Studio 遥测，日志记录也会被禁用。

1. 电子邮件：可以直接向团队发送反馈，地址是 rtvsuserfeedback@microsoft.com。
