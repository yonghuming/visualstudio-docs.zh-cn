---
title: "在 Visual Studio 中使用 PyLint | Microsoft Docs"
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc668a4b-10ae-4199-90b8-c984456b6003
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
translationtype: Human Translation
ms.sourcegitcommit: 9328c347d548a03a536cea16bd5851817c03d5a2
ms.openlocfilehash: c8bfaf9f20e7fecb3633ca101170b0f3e686aa53
ms.lasthandoff: 04/10/2017

---

# <a name="using-pylint-to-check-python-code"></a>使用 PyLint 检查 Python 代码

[PyLint](https://www.pylint.org/) 是一种广泛使用的工具，当前已集成到 Visual Studio for Python 项目中，可用于检查 Python 代码中的错误以及促进建立良好的 Python 编码模式。

右键单击解决方案资源管理器中的 Python 项目，并选择“Python”>“运行 PyLint...”：

![用于 Python 项目的上下文菜单上的 PyLint 命令](~/docs/python/media/code-pylint-command.png)

如有需要，使用命令提示符将 PyLint 安装到活动环境。

PyLint 警告和错误显示在“错误列表”窗口：

![PyLint 错误列表](~/docs/python/media/code-pylint-error-list.png)

双击错误可直接转到出现问题的源代码。

> [!Tip]
> 有关所有 PyLint 输出消息的详细列表，请参阅[PyLint 功能参考](https://pylint.readthedocs.io/en/latest/reference_guide/features.html)。

## <a name="setting-pylint-command-line-options"></a>设置 PyLint 命令行选项

PyLint 文档中的[命令行选项](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options)部分介绍了如何通过 `.pylintrc` 配置文件控制 PyLint 的行为。 此类文件可置于 Visual Studio 中的 Python 项目的根路径中，或其他地方，具体取决于想要应用这些设置的范围。

例如，若要使用项目中的 `.pylintrc` 文件禁止显示上图所示的“缺少 docstring”警告，请执行以下操作：

1. 使用命令行导航到项目根路径（在此可找到 `.pyproj` 文件），并运行以下命令以生成已注释的配置文件：

   ```bash
   pylint --generate-rcfile > .pylintrc
   ```

1. 在 Visual Studio 解决方案资源管理器中，右键单击项目，选择“添加”>“退出项...”，导航到新的 `.pylintrc` 文件，并选中该文件，然后选择“添加”。

1. 打开要编辑的文件，将看到可以使用的各种设置。 若要禁用警告，请找到 `[MESSAGES CONTROL]` 部分，然后找到其下的 `disable` 设置。 你将看到特定消息的一条长字符串，可以向其追加所需的任何警告。 在此例中，追加 `,missing-docstring`（包括界定逗号）。

1. 保存 `.pylintrc` 文件，然后重新运行 PyLint 以查看现在禁止显示的警告。
