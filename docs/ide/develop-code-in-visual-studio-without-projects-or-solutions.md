---
title: "在 Visual Studio 中开发代码而无需创建项目或解决方案 | Microsoft Docs"
ms.custom: 
ms.date: 02/27/2017
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
- code, editing
- code editor, syntax coloring
- code editor [Visual Studio]
- brace matching
- code editor, line numbers
- code editor, brace matching
- line numbers
- syntax coloring
- code editor
- code files
- code
ms.assetid: cb53bb9b-5b76-4759-b9b8-7bf32298bcbb
caps.latest.revision: 44
author: kempb
ms.author: kempb
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
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 3a8be04b4d2c927dc296753420ff736b993343c9
ms.lasthandoff: 03/07/2017

---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>在 Visual Studio 中开发代码而无需创建项目或解决方案

在 Visual Studio 2017 中，你可以在 Visual Studio 中打开几乎任何类型的基于目录的项目的代码，而无需创建解决方案或者项目文件。 这意味着（例如，在 Git 上找到一个代码项目时）可以克隆该项目，然后在 Visual Studio 中直接打开并开始开发，而无需创建解决方案或项目。

不仅可以在 Visual Studio 中编辑并生成代码，还能在代码中导航（例如通过 Navigate To 命令）。 代码带有语法着色，许多情况下还含有基本的语句完成和调试以及断点。 有些语言甚至会包含更多的功能。 请参阅[创建可移植的自定义编辑器设置](create-portable-custom-editor-options.md)，了解详细信息。

## <a name="open-code-anywhere"></a>在任意位置打开代码
可以通过以下方式，在 Visual Studio 中打开代码。
- 在 Visual Studio 菜单栏上，依次选择“文件”**、**“打开”**、**“文件夹”，然后浏览到代码位置。
- 在包含该代码的文件夹的上下文（右键单击）菜单上，选择“在 Visual Studio 中打开”命令。
- 选择 Visual Studio“开始”页上的“打开文件夹”链接。
- 打开从 GitHub 存储库中克隆的代码。

以下示例演示如何克隆 GitHub 存储库，并在 Visual Studio 中打开其代码。 若要执行此过程，必须具有 GitHub 帐户，并且已经在系统上安装了适用于 Windows 的 Git。 请参阅[注册新的 GitHub 帐户](https://help.github.com/articles/signing-up-for-a-new-github-account/)和[适用于 Windows 的 Git](https://git-for-windows.github.io/) 了解详细信息。

### <a name="to-open-code-from-a-cloned-github-repo"></a>打开克隆的 GitHub 存储库中的代码

1. 转到包含你要处理的代码的 GitHub 存储库。 为此，你需要一个 GitHub 帐户。
1. 转到想要克隆的存储库。
1. 在存储库的 GitHub 页上，选择“克隆或下载”按钮，然后在下拉菜单中选择“复制到剪贴板”按钮，以便复制 GitHub 网站的安全 URL。

  ![GitHub 克隆按钮](~/docs/ide/media/VSIDE_Code_Clone.png)

    > [!NOTE]
    >  本示例演示如何通过使用安全 URL 方法克隆存储库，但是你也可以选择在桌面上打开项目，或者下载项目的 .zip 文件。

1. 在 Visual Studio 中，选择“团队资源管理器”选项卡，打开团队资源管理器。
1. 在团队资源管理器的“本地 Git 存储库”部分中，选择“克隆”命令，然后将 GitHub 页的 URL 粘贴到文本框。

  ![克隆项目](~/docs/ide/media/VSIDE_Code_Clone2.png)

1. 选择“克隆”按钮，将项目的文件克隆到本地 Git 存储库。 此过程可能需要几分钟的时间，具体取决于存储库的大小。
1. 将存储库克隆到系统后，在“团队资源管理器”中，在新克隆项目的上下文（右键单击）菜单上，选择“打开”命令。

  ![克隆的项目](~/docs/ide/media/VSIDE_Code_Clone3.png)

1. 选择“显示文件夹视图”命令，查看解决方案资源管理器中的文件

  ![显示文件夹视图](./media/VSIDE_Code_Clone3_show.png)

  此时，可以浏览克隆项目中的文件夹和文件，并在具有语法着色和其他功能的 Visual Studio 代码编辑器中查看和搜索代码。

    ![搜索克隆项目的代码](~/docs/ide/media/VSIDE_Code_Clone4.png)


## <a name="debug-your-code"></a>调试代码
可以在 Visual Studio 中调试代码。 对某些语言进行调试时，可能需要在代码项目中指定一个有效的*启动文件*，例如脚本、可执行文件或项目。 调试代码时，Visual Studio 会首先运行此指定代码。

工具栏上“开始”按钮旁的下拉列表框中列出了 Visual Studio 检测到的所有启动项，以及你在文件夹中专门选择的项。

![运行按钮](~/docs/ide/media/VSIDE_Code_Run_Button.png)

Visual Studio 会自动识别项目，但是需要你将脚本（例如 Python 和 JavaScript）显式选择为启动项之后，项目才会出现在列表中。
此外，某些启动项（例如 MSBuild 和 CMake）可能有多个生成配置，这些生成配置会显示在运行按钮的下拉列表中。

Visual Studio 目前支持对下列语言进行调试：
- Node.js
- Python
- 基于 MSBuild 的项目（C#、VB、C++）
- 所有带有 PDB（Python 调试器）的可执行文件。

### <a name="to-debug-nodejs-and-python"></a>调试 Node.js 和 Python：
1. 安装 Node.js 或 Python 工具或 Visual Studio 2017 和 Node.js 运行时。
1. 在解决方案资源管理器中的 JavaScript 文件的上下文菜单上，选择“设置为启动项”命令。
1. 选择 F5 键开始调试。

### <a name="to-debug-msbuild-projects"></a>调试 MSBuild 项目
1. 在 Visual Studio 菜单上，选择“调试”。 在下拉列表菜单上，选择该项目，或者选择想要在解决方案资源管理器中显示为启动项的项目或文件。
1. 选择 F5 键开始调试。

### <a name="to-debug-executable-files"></a>调试可执行文件
1. 在 Visual Studio 菜单上，选择“调试”。 在下拉列表菜单上，选择该项目，或者选择想要在解决方案资源管理器中显示为启动项的项目或文件。
1. 选择 F5 键开始调试。


## <a name="enable-custom-build-tools"></a>启用自定义生成工具
Visual Studio 可以运行多种语言，但它不能运行所有语言。 如果 Visual Studio 可运行你的语言，你可以立即开始运行代码。 如果 Visual Studio 无法运行你尝试运行的代码，信息栏会提示你指定基本代码中的某个文件作为启动项。

如果 Visual Studio 无法识别基本代码使用的自定义生成工具，则可能无法在 Visual Studio 中运行和调试代码（例如通过选择 F5 键），除非你指定了有效的可执行文件类型（例如编译器）和该语言所需要的所有自定义参数和自变量。 为此，Visual Studio 提供生成任务。 可以通过创建生成任务来指定语言生成和运行此代码所需的所有项。

还可以通过创建任意的生成任务来执行你所需的几乎所有操作。 例如，可以创建一个任务来列出文件夹的内容或者重命名文件。 也可以创建针对性更强的自定义生成任务，例如使用特定自变量来编译和生成项目。 以下步骤演示了如何创建两种类型的生成任务。

#### <a name="to-create-an-arbitrary-build-task"></a>创建任意的生成任务

1. 在解决方案资源管理器中，选择要创建任务的项目的文件或文件夹，在文件或文件夹的上下文（右键单击）菜单上，选择“配置任务”。

  ![配置任务](~/docs/ide/media/VSIDE_Code_Config_Task.png)

  选择“配置任务”可打开名为 tasks.vs.json 的文件。 如果此文件不存在，系统将创建此文件。 此文件中包含所选文件或文件夹的生成任务。

  ![Tasks.vs.json 文件](~/docs/ide/media/VSIDE_Code_Tasks_JSON.png)

1. 将以下生成任务添加到 tasks.vs.json。 此示例中，我们将添加一个名为“列出输出”的简单任务，该任务将在输出窗口中列出所选文件夹中的文件和子文件夹。 （新任务将添加到现有的“任务”数组中。）

  ```xml
      {
        "taskName": "List outputs",
        "appliesTo": "*",
        "type": "command",
        "command": "${env.COMSPEC}",
        "args": [
          "dir ${outDir}"
        ]
      },
  ```
  完整的生成任务应如下所示。

  ![任意的生成任务](~/docs/ide/media/VSIDE_Code_Tasks_ArbTask.png)

1. 保存项目。
1. 打开所选文件夹的上下文菜单。 应该可以在上下文菜单底部看到新的任意生成任务。

  ![任意生成任务命令](~/docs/ide/media/VSIDE_Code_Tasks_ArbTask2.png)

1. 通过选择新的“列出输出”命令来执行该任务。


### <a name="to-create-a-custom-build-task"></a>创建自定义生成任务
在此过程中，我们将添加两个自定义生成任务，这两个任务使用 nMake 来生成和清除代码。

1. 在解决方案资源管理器中，选择项目文件，我们之后会将该文件指定为启动项。 在该文件的上下文（右键单击）菜单上，选择“配置任务”。

  ![自定义生成任务命令](~/docs/ide/media/VSIDE_Code_Tasks_CustTask1.png)

1. 将以下生成任务添加到 tasks.vs.json。 本示例中，我们将添加两个任务：一个任务名为“makefile-build”，该任务使用 nMake 命令来生成项目；另一个任务名为“makefile-clean”，该任务调用带有“clean”自变量的 nMake 命令。 应将这两个任务添加到现有的“任务”数组中。 （请注意，这些仅是生成任务的示例。 要使其生效，还需要在系统上安装包含 [nNake](https://docs.microsoft.com/en-us/cpp/build/nmake-reference) 的工作负载。）

  ```xml
  {
  "taskName": "makefile-build",
  "appliesTo": "makefile",
  "type": "command",
  "contextType": "build",
  "command": "nmake"
  },
  {
  "taskName": "makefile-clean",
  "appliesTo": "makefile",
  "type": "command",
  "contextType": "clean",
  "command": "nmake",
  "args": [
    "clean"
    ]
  },
  ```
  完整的自定义生成任务应如下所示。

  ![自定义生成任务](~/docs/ide/media/VSIDE_Code_Tasks_CustTask2.png)

1. 保存项目。
1. 打开所选文件的上下文菜单。 新的自定义生成任务应该出现在上下文菜单的中间位置。

  ![自定义生成任务命令](~/docs/ide/media/VSIDE_Code_Tasks_CustTask3.png)

  > [!NOTE]
  > 由于命令的 `contextType` 设置，命令显示在“配置任务”命令下；“build”和“clean”是生成命令，因此它们出现在上下文菜单中间位置的生成部分。

  将自定义生成命令与文件相关联后，可以将该文件指定为启动项。

1. 在文件的上下文菜单中，选择“设置为启动项”。

  ![自定义生成任务命令](~/docs/ide/media/VSIDE_Code_Tasks_CustTask4.png)

1. 在工具栏上，选择“开始”按钮旁边的下拉箭头。 启动项现在显示为一个选项。

  ![自定义生成任务命令](~/docs/ide/media/VSIDE_Code_Tasks_CustTask5.png)

现在可以通过选择“开始”按钮或者 F5 键来运行基础代码。 即使 Visual Studio 无法识别基本代码的生成工具，也可以在 Visual Studio 中编辑和调试基本代码。 生成任务的输出将显示在“输出”窗口中，而生成错误将显示在“错误列表”中。 tasks.vs.json 生成任务文件将 Visual Studio 内部开发循环与基本代码所使用的自定义生成工具紧密结合起来。

可以将自定义生成任务添加到单个文件，也可以将其添加到某个特定类型的所有文件。 例如，可以将 NuGet 包文件配置为具有“还原包”任务，也可以将所有源文件配置为具有静态分析任务，例如所有 .js 文件的 linter。

除了环境变量（例如 `$env.var`）或键外，Visual Studio 还支持 tasks.vs.json 根目录中的 VSCode `$variable` 替换。

## <a name="specify-build-output"></a>指定生成输出
如果需要对项目进行编译，可以在 tasks.vs.json 文件中添加名为 `output` 的额外标记。 这是一个示例。

`"output": "${workspaceRoot}\\bin\\hellomake.exe"`

通过指定输出位置，可向 Visual Studio 指示项目生成输出的位置。


## <a name="tasksvsjson-file-location"></a>Tasks.vs.json 文件位置

默认情况下，tasks.vs.json 文件位于一个名为 `.vs` 的隐藏文件夹中。 若要在 Visual Studio 中查看隐藏文件夹，请在解决方案资源管理器工具栏上选择“显示所有文件”按钮。

![任意生成任务命令](~/docs/ide/media/VSIDE_Code_Tasks_FileLocation.png)

tasks.vs.json 文件通常是隐藏状态，因为一般情况下大多数用户不希望在源控件中打开该文件。 但是如果要在源控件中打开该文件，请将其拖入项目的根目录，此处将显示该文件。

.vs 文件夹中可能存在其他 .json 文件，但唯一需要移动的文件是 tasks.vs.json 文件和 launch.vs.json 文件（如果存在）。 launch.vs.json 文件用于配置 Visual Studio 调试器，而 tasks.vs.json 文件用于配置 Visual Studio 中的生成。

