---
title: "开始使用 Visual Studio 中的 Pytho | Microsoft Docs"
ms.custom: 
ms.date: 5/1/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9087b19-275b-4cc1-8d0c-f9c4356c9ce8
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
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 8001036077b8b14af80fabceafad5d3aff9b25f4
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---

# <a name="getting-started-with-python-in-visual-studio"></a>Visual Studio 中的 Python 入门

安装了附带 Python 工作负荷的 Visual Studio (Visual Studio 2017) 或附带针对 Visual Studio 的 Python 工具的 Visual Studio（Visual Studio 2015 及更早版本）后，便可以介绍 Python 开发体验。 （如果需要，请参阅[安装](installation.md)。）

在本演练中，将创建新的空 Python 应用程序，选择要配合使用的 Python 环境，然后开始编写一些代码以查看工作中的 IntelliSense。 然后与交互式 REPL 窗口短时间配合使用以创建更多代码，再完成该程序，并通过其本身和调试器运行该程序。

> [!Note]
> 本演练介绍了 Visual Studio 2017 中的 Python 体验；其他版本类似，但细节部分可能会有所不同。

## <a name="create-a-new-python-project"></a>创建新的 Python 项目

Visual Studio 中的 Python 支持包括大量的[项目模板](python-projects.md)，便于开始使用不同类型的项目，包括将 Bottle、Flask 和 Django 框架与 Azure 云服务一起使用的 Web 应用程序。 但为了便于演示，我们将以空项目开始。

1. 在 Visual Studio 中，选择“文件”>“新建项目”，这会打开“新建项目”对话框。 可在此处浏览并选择模板，并指定要在其中创建项目的文件夹。

1. 可在左侧的“模板”>”其他语言”>“Python”下或只需搜索“Python”即可找到 Python 模板：

    ![显示 Python 项目的新建项目对话框](media/getting-started-new-project.png)

1. 选择“Python 应用程序”模板，为项目指定文件夹并选择“确定”。 （如果想要立即为项目创建本地存储库，还需选择“添加到源控件”选项）。

    > [!Tip]
    > 通过“基于现有的 Python 代码”模板，可快速从已包含 Python 代码的文件夹中创建 Visual Studio 项目，而不是创建新的空项目并将现有代码导入其中。

1. 几分钟后，将看到该项目在 Visual Studio 解决方案资源管理器窗口中打开。 在此处可以浏览项目中的文件和文件夹，也可以管理环境。

    ![具有 Python 项目的解决方案资源管理器](media/getting-started-solution-explorer-1.png)

1. 展开“Python 环境”节点，将会看到此项目当前默认的 Python 解释器。 如果同时展开该解释器节点，将看到该环境中可用的库列表：

    ![显示 Python 环境的解决方案资源管理器](media/getting-started-solution-explorer-2.png)

1. 如果使用 Visual Studio 2015 或更早版本，则不会默认安装 Python 解释器。 请参阅[选择并安装 Python 解释器](python-environments.md#selecting-and-installing-python-interpreters)，了解此过程。

### <a name="going-deeper"></a>深入了解

- [Visual Studio 中的 Python 项目](python-projects.md)。
- [Web 项目模板](template-web.md)
- [Django Web 项目模板](template-django.md)
- [Azure 云服务模板](template-azure-cloud-service.md)

## <a name="writing-and-running-code"></a>编写和运行代码

1. 创建新的“Python 应用程序”项目后，名为 `PythonApplication1.py` 的默认空文件将在 Visual Studio 编辑器中打开。 若要将其重命名，请在解决方案资源管理器中右键单击该文件，选择“重命名”，将名称更改为 `hello.py`。

1. 开始键入 `print("Hello world")`，注意 Visual Studio IntelliSense 如何在此过程中显示自动完成选项。 下拉列表中加外边框的选项是按 Tab 键时使用的默认完成选项。 涉及到较长的语句或标识符时，可以使用该选项。

    ![IntelliSense 自动完成弹出窗口](media/getting-started-coding-1.png)

1. IntelliSense 根据正在使用的语句、正在调用的函数等显示不同的信息。 使用 `print` 函数时，键入 `(` 进行调用可弹出有关该函数的完整用法信息，甚至可以对需要提供的当前参数进行加粗（如此处所示的 **value**）：

    ![某函数的 IntelliSense 自动完成弹出窗口](media/getting-started-coding-2.png)

1. 完成该语句，使其与以下内容匹配：

  ```python
  print("Hello world")
  ```

1. 若要运行此代码，请在下面所示的工具栏上选择“开始”按钮，按 F5 或选择“调试”>“开始调试”菜单项。

    ![调试工具栏上的“开始”按钮](media/getting-started-coding-3.png)

    > [!Note]
    > 如果在 Visual Studio 2015 或更早版本中看到一条消息 - 不存在任何解释器，请参阅[选择并安装 Python 解释器](python-environments.md#selecting-and-installing-python-interpreters)（因为默认未安装 Python 解释器）。

1. Visual Studio 将使用默认环境在项目中运行代码，并在命令窗口中显示结果。 按某个键关闭该窗口并结束调试会话。

    ![调试工具栏上的“开始”按钮](media/getting-started-coding-4.png)

1. 除了语句和函数外，IntelliSense 还提供 `import` 语句的完成。 这有助于轻松发现环境中可用的模块以及模块中可用的成员。 在编辑器中，删除 `print` 行，开始键入 `import`。 将看到一个模块列表出现：

    ![显示 import 语句的可用模块的 IntellSense](media/getting-started-coding-5.png)

1. 通过键入或选择 `sys` 完成行。

1. 在下一行中，键入 `from` 再次查看模块列表：

    ![显示 from 语句的可用模块的 IntellSense](media/getting-started-coding-6.png)

1. 选择或键入 `math`，然后继续键入一个空格和 `import`，将显示模块成员：

    ![显示模块成员的 IntellSense](media/getting-started-coding-7.png)

1. 通过导入 `sin`、`cos` 和 `radians` 成员完成，注意自动完成可用于每个成员。 完成后，代码应如下所示：

  ```python
  import sys  
  from math import sin, cos, radians          
  ```

> [!Tip]
> 完成可处理键入时的子字符串，匹配单词的某些部分、单词开头的字母，甚至是跳过的字符。 请参阅[编辑代码 - 完成](code-editing.md#completions)，了解详细信息。

在下一步，我们将使用交互式 REPL 窗口编写一些可在不运行调试器的情况下立即进行测试的代码。

### <a name="going-deeper"></a>深入了解

- [编辑代码](code-editing.md)
- [设置代码格式](code-formatting.md)
- [重构代码](code-refactoring.md)
- [使用 PyLint](code-pylint.md)


## <a name="using-the-interactive-repl-window"></a>使用交互式 REPL 窗口

适用于 Python 的 Visual Studio 交互窗口提供丰富的“读取-评估-输出-循环”体验，极大地缩短了常用的“编辑-生成-调试”周期。 它类似于 Python 命令行的 REPL 体验，但提供了一些附加功能，如此处所示。

1. 通过从 Visual Studio 主菜单选择“视图”>“其他窗口”>“Python 交互窗口”打开交互窗口。 该窗口打开时，出现常用的 >>> Python REPL 提示符。 请注意，你可以随时使用工具栏上的下拉列表菜单更改环境：

    ![Python 交互窗口](media/getting-started-interactive-1.png)

1. 输入几个语句（如 `print("hello")`）和表达式（如 `123/567`）即可查看即时结果：

    ![Python 交互窗口即时结果](media/getting-started-interactive-2.png)

1. 开始编写多行语句（例如函数定义）时，交互窗口将针对后续行显示 ... 提示符，它与命令行 REPL 不同，可以提供自动缩进：

    ![含语句后续符的 Python 交互窗口](media/getting-started-interactive-3.png)

1. 交互窗口提供所有已输入内容的完整历史记录，并通过多行历史记录项改进了命令行 REPL。 例如，你可以轻松地将上述 `f` 函数的整个定义重新调用为单个单元，并轻松地将名称更改为 `make_double`，而不是逐行重新创建函数。

1. 另一个非常有用功能是能够将多行代码从编辑器窗口快速发送至交互窗口，然后可以在快速 REPL 环境中处理它，而不是编写在调试器中运行的其他代码。 若要了解这一点，首先将以下代码添加到在编辑器中打开的 hello.py 文件：

  ```python
  def make_dot_string(x):  
      return ' ' * int(10 * cos(radians(x)) + 10) + 'o'
  ```

1. 选择 hello.py 中的所有代码（包括 `import` 语句），单击右键，选择“发送到交互”(Ctrl+Enter)。 代码将立即粘贴至交互窗口并运行。 由于代码定义了一个函数，因此可通过数次调用它来快速测试该函数：

    ![将代码发送到交互窗口](media/getting-started-interactive-4.png)

1. 使用“发送到交互窗口”，可有效地将多行代码（如联机查找的内容）粘贴到交互窗口中，而此操作无法直接完成。 例如，复制以下代码，尝试将其粘贴 (Ctrl+V) 到交互窗口中，可以看到没有任何反应。 但可以将其粘贴到编辑器中，选择它，然后使用“发送到交互”命令即可看到其运行。

  ```python
  for i in range(360):
      s = make_dot_string(i)  
      print(s) 
  ```

    ![使用“发送到交互窗口”粘贴多行代码](media/getting-started-interactive-5.png)

1. 因为函数定义再次在 REPL 历史记录中作为单个单元，因此可轻易返回并进行任何所需的更改，然后再次测试函数。

1. 如果对编写的代码感到满意，可在交互窗口中选择代码，单击右键，选择“复制代码”，然后粘贴到编辑器中。 “复制代码”命令的特殊功能是，它会自动忽略任何输出以及 >>> 和 ... 提示文本。 例如，将此命令用于以下所示的选择内容：

  ![交互窗口复制代码命令](media/getting-started-interactive-6.png)

  仅粘贴以下内容：

  ```python
  make_dot_string(180)
  make_dot_string(135)
  for i in range(360):
      s = make_dot_string(i)  
      print(s) 
  ```

1. 最后，交互窗口提供许多元命令，允许你加载文件、在不丢失历史记录的情况下重置环境，以及在继续操作的过程中插入注释。 请参阅[交互窗口 - 元命令](interactive-repl.md#meta-commands)，了解详细信息。

### <a name="going-deeper"></a>深入了解

- [使用交互窗口](interactive-repl.md)
- [使用 IPython REPL](interactive-repl-ipython.md)

## <a name="running-code-in-the-debugger"></a>在调试器中运行代码

除了管理项目、提供丰富的编辑体验和交互窗口外，Visual Studio 还对 Python 代码提供其功能全面的调试支持。

1. 编辑 hello.py 文件中的代码，使其与以下代码匹配：

  ```python  
  from math import sin, cos, radians  
  import sys  
    
  def make_dot_string(x):  
      return ' ' * int(10 * cos(radians(x)) + 10) + 'o'  
    
  def main():  
      for i in range(360 * 5):
          s = make_dot_string(i)  
          print(s)  
            
  main()
  ```  

1. 选择工具栏上的“开始”、按 F5 或选择“调试”>“开始调试”菜单命令，检查代码是否正常运行。 这将在调试器中运行代码，但由于我们没有设置任何断点，因此对于几次迭代你只会看到波浪图案。 此时，按任意键将关闭输出窗口。

    > [!Tip]
    > 若要在程序完成时自动关闭输出窗口，请使用以下代码替换 `main()` 调用：
    >
    > ```python    
    > if __name__ == "__main__":  
    >     sys.exit(int(main() or 0))      
    > ```
    > 
    > 或者，如果曾遇到输出窗口意外自动关闭的情况，请右键单击项目，选择“属性”，选择“调试”选项卡，然后将 `-i` 添加到**解释器参数**字段。 这会导致解释器在程序完成后进入交互模式，从而使窗口保持打开状态，直到按 Ctrl+Z, Enter 退出为止。

1. 要在 `main` 函数的第一行上设置断点，可通过单击该行左侧的灰色边距，或将插入符号置于该行并使用“调试”>“切换断点”*命令 (F9) 实现。 将在灰色边距中显示一个红点来表示该断点（如以下蓝色箭头标记所示）：

    ![设置断点](media/getting-started-debugging-1.png)

1. 再次启动调试器，将看到代码运行至包含该断点的行处停止。 可在此处查看调用堆栈，并在局部变量窗口中检查局部变量：

    ![Python 的断点 UI 体验](media/getting-started-debugging-2.png)

1. 使用 F10、“调试”>“单步跳过”命令或“单步跳过”工具栏按钮逐行执行 `for` 循环的几次迭代。 这意味着调试器将运行对 `make_dot_string` 的每个调用，但不会在该函数内部停止（除非设置断点）。

1. 在工具栏中，下面显示的三个执行按钮从左到右依次是：单步执行、单步跳过和单步跳出：

    ![执行工具栏按钮](media/getting-started-debugging-3.png)

1. 使用单步执行命令 (F11) 立即单步执行 `make_dot_string`。 将看到从 `for` 循环执行到该函数。 再次执行将返回到 `for` 循环，但如果函数中有其他行，需要逐个执行。 如果正在函数中，且想要运行其行的其余部分并返回到调用代码，请使用单步跳出 (Shift+F11)。

1. 若要继续运行代码，直到下一个断点（或程序结束），请再次按 F5 或者选择“继续”工具栏按钮或“调试”>“继续”。 因为 `for` 循环中有断点，因此下一次迭代将中断。

1. 逐句通过循环的上百次迭代可能会很单调，因此可向之前设定的断点添加条件，使其仅在 `i` 的值超过特定值（例如 1600）时中断。 为此，请右键单击红色断点，选择“条件...”。 在显示的“断点设置”窗口中，输入 `i > 1600` 作为表达式，选择“关闭”。 现在，按 F5 继续，将看到程序再次中断前运行了一段时间。 

    ![设定断点条件](media/getting-started-debugging-4.png)

1. 若要完成程序，可再次切换断点，然后按 F5。 完成调试后，Visual Studio 将返回到其编辑模式。

### <a name="going-deeper"></a>深入了解

- [调试](debugging.md)。
- 另请参阅 [Visual Studio 中调试](../debugger/debugging-in-visual-studio.md)，了解 Visual Studio 调试功能的完整文档。

## <a name="next-steps"></a>后续步骤

除了前面提供的“深入了解”链接外，以下主题还介绍了 Visual Studio 中 Python 体验的其他功能：

- 若要查看 Visual Studio 如何连接到 Azure 应用服务，请参阅[将 Python Web 应用程序发布到 Azure](publishing-to-azure.md)
- 若要了解如何全局管理以及针对单个项目管理不同的环境（包括虚拟环境），请参阅 [Python 环境](python-environments.md)。
- 使用 Visual Studio 能够在远程服务器上调试应用程序，如[跨平台远程调试](debugging-cross-platform-remote.md)和 [Azure 远程调试](debugging-azure-remote.md)中所述。
- 可使用 [Visual Studio 分析](profiling.md)评估 Python 代码的性能。
- 如[单元测试](unit-testing.md)中所述，将使用 Python 编写的单元测试直接与 Visual Studio 测试资源管理器集成。
- [Microsoft Virtual Academy 上的免费 Phthon 课程](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)

