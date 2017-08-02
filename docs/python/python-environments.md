---
title: "Visual Studio 中的 Python 环境| Microsoft Docs"
ms.custom: 
ms.date: 5/8/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8876f8c1-4770-44dc-97d8-bf0035ae8196
caps.latest.revision: 11
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
ms.openlocfilehash: 9140ca7549eefc3ac221f3ca0aa54fde482c8623
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---

# <a name="python-environments"></a>Python 环境

Visual Studio 中的 Python 使管理多个 Python 环境更加简单，并且对于不同的项目可轻松在各环境间切换。 

注意：如果是初次使用 Visual Studio 中的 Python，请首先参阅以下主题，其中提供了相关内容的讨论：

- [在 Visual Studio 中使用 Python](python-in-visual-studio.md)
- [安装针对 Visual Studio 的 Python 支持](installation.md)

始终运行 Python 代码的 Python *环境* 由解释器、库（通常是 Python 标准库）以及一组已安装的包组成。 这些内容共同确定哪些语言结构和语法有效、哪些操作系统功能可访问以及哪些程序包可使用。

在 Visual Studio 中，环境还包括一个用于环境的库的 IntelliSense 数据库，这样一来，在 Visual Studio 中键入类似 `import` 的语句将自动显示可用库以及这些库内的模块的列表。

开发人员通常只使用单一的全局 Python 环境，但如本主题中所述，有些情况需要管理多个全局环境、特定于项目的环境，或许还有虚拟环境：

- [选择并安装 Python 解释程序](#selecting-and-installing-python-interpreters)
- [在 Visual Studio 中管理 Python 环境](#managing-python-environments-in-visual-studio)
- [全局环境](#global-environments)
- [特定于项目的环境](#project-specific-environments)
- [虚拟环境](#virtual-environments)
- [管理所需的包](#managing-required-packages)
- [搜索路径](#search-paths)

有关视频介绍，请参阅[深度分析：Python 解释器](https://youtu.be/KY1GEOo3qy0)（youtube.com，13m27s）。

> [!VIDEO https://www.youtube.com/embed/KY1GEOo3qy0]

## <a name="selecting-and-installing-python-interpreters"></a>选择并安装 Python 解释程序

Python 支持除了随 Visual Studio 2017 提供外，并未随 Python 解释器提供，因此需要安装以下解释器之一才能运行代码。 一般情况下，Visual Studio 将自动检测新安装的解释器，并为其设置环境。 如果它并未执行这些操作，请参阅下面的[为现有解释器创建环境](#creating-an-environment-for-an-existing-interpreter)。

| 解释器 | 说明 | 
| --- | --- | 
| [CPython](https://www.python.org/) | 最常用的“本机”解释器，32 位和 64 位版本可用（建议使用 32 位）。 包括最新的语言功能、最大的 Python 包兼容性、完整的调试支持以及与 [IPython](http://ipython.org/) 的互操作。 另请参阅：[应使用 Python 2 还是 Python 3？](http://wiki.python.org/moin/Python2orPython3) |
| [IronPython](http://ironpython.codeplex.com/) | Python 的 .NET 实现，32 位和 64 位版本可用，提供 C#/F#/Visual Basic 互操作、对 .NET API 的访问、标准 Python 调试（但不是 C++ 混合模式调试）和混合 IronPython/C# 调试。 但 IronPython 不支持虚拟环境。 | 
| [Anaconda](https://www.continuum.io) | Python 提供技术支持的开放式数据科学平台，包括最新版本的 CPython 和大部分难以安装的包。 如果你不能做出决定，我们建议使用它。 |
| [PyPy](http://www.pypy.org/) | Python 的高性能跟踪 JIT 实现，适用于长时间运行的程序以及识别性能问题但找不到其他解决方法的情况。 可与 Visual Studio 配合使用，但对高级调试功能的支持有限。 |
| [Jython](http://www.jython.org/) | Java 虚拟机 (JVM) 上 Python 的实现。 与 IronPython 类似，Jython 中运行的代码可与 Java 类和库交互，但可能无法使用许多适用于 CPython 的库。 可与 Visual Studio 配合使用，但对高级调试功能的支持有限。 |

对于想要提供新形式的 Python 环境检测的开发人员，请参阅 [PTVS 环境检测](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (github.com)。

## <a name="managing-python-environments-in-visual-studio"></a>在 Visual Studio 中管理 Python 环境

若要打开 Python 环境窗口，请执行以下操作之一：

1. 选择“查看”>“其他窗口”>“Python 环境”菜单命令。
1. 在解决方案资源管理器中右键单击某项目的“Python 环境”，选择“查看所有 Python 环境”：

    ![解决方案资源管理器中的“查看所有环境”命令](~/python/media/environments-view-all.png)
    
在任一情况下，Python 环境窗口都显示为解决方案资源管理器的同级选项卡：

![“Python 环境”窗口](~/python/media/environments-default-view.png)

上述示例显示 Python 3.4（32 位 CPython）与 32 位和 64 位版本的 IronPython 2.7 一起安装。 在这种情况下，粗体显示的默认环境是 Python 3.4，将对任何新项目使用它。 如果未看到任何环境列出，表示已安装针对 Visual Studio 2015 或更早版本中的 Visual Studio 的 Python 工具，但尚未安装 Python 解释器（请参阅上述[选择并安装 Python 解释器](#selecting-and-installing-python-interpreters)）。 

> [!Tip]
> **Python 环境*窗口较窄时（如上所示），环境在顶部列出和各选项卡在底部列出。 如果将窗口展开足够大，就可以看到较宽的视图，这可能处理起来更方便。
>
> ![“Python 环境”窗口扩展后的视图](~/python/media/environments-expanded-view.png)

> [!Note]
> 尽管 Visual Studio 遵循系统-站点-包选项，但它没有提供从 Visual Studio 中更改它的方法。

### <a name="creating-an-environment-for-an-existing-interpreter"></a>为现有解释器创建环境

Visual Studio 通常通过检查注册表来查找已安装的 Python 解释器，但如果解释器以非标准的方式安装，它可能找不到它。 在这种情况下，可以如下所示，将 Visual Studio 直接指向解释器：

1. 在环境窗口中选择“+ 自定义...”，这将创建一个新环境，然后打开[“配置”选项卡](#configure-tab)（如下所示）。

    ![新自定义环境的默认视图](~/python/media/environments-custom-1.png)

1. 在“说明”字段中为该环境输入名称。
1. 在“前缀路径”字段输入或浏览到解释器的路径。
1. 选择“自动检测”让 Visual Studio 完成余下的字段，或手动完成它们。
1. 选择“应用”保存环境。
1. 如果需要删除环境，请在“配置”选项卡上选择“删除”命令。

### <a name="overview-tab"></a>概述选项卡

提供环境的基本信息和命令，如将其设置为默认、使用该环境打开[交互式 (REPL) 窗口](interactive-repl.md)以及跳转到配置交互式窗口的对话框（等同于“工具”>“选项”菜单命令，选择“Python 工具”>“交互式窗口”和该环境的名称）。

![Python 环境概述选项卡](~/python/media/environments-overview-tab.png)

> [!Note]
> 更改活动环境可能会导致加载 IntelliSense 数据库时，Visual Studio 短时间无响应。 含有多个包的环境可能无响应的时间更长。

### <a name="configure-tab"></a>配置选项卡

如果显示，其中包含如下表中所述详细信息。 如果此选项卡不显示，意味着 Visual Studio 自动管理所有详细信息。

![Python 环境配置选项卡](~/python/media/environments-configure-tab.png)

| 字段 | 说明 |
| --- | --- |
| **描述** | 为环境提供的名称。 |
| **前缀路径** | 解释程序的基本文件夹位置。 填写此项并单击“自动检测”，Visual Studio 会尝试为你填充其他字段。 |
| **解释器路径** | 解释器可执行文件的路径，通常是前缀路径后加 `python.exe` |
| **窗口化解释器** | 非控制台可执行文件的路径，通常是前缀路径后加 `pythonw.exe`。 |
| **库路径** | 指定标准库的根，但如果 Visual Studio 能够从解释器请求更准确的路径，可能会忽略此值。 |
| **语言版本** | 从下拉菜单中选定。 |
| **体系结构** | 通常自动检测并进行填充，否则指定 32 位或 64 位。 |
| **路径环境变量** | 解释器用来查找搜索路径的环境变量。 启动 Python 时 Visual Studio 更改该变量的值，使其包含项目的搜索路径。 此属性通常应设置为 `PYTHONPATH`，但某些解释器使用不同的值。 |

### <a name="pip-tab"></a>pip 选项卡

管理环境中安装的包，还允许你搜索并安装新的包（包括任何依赖项）。 搜索功能将筛选当前已安装的包，也会搜索 [PyPI](https://pypi.python.org)。 还可以在搜索框中直接输入任何 `pip install` 命令，包括标志（例如 `--user` 或 `--no-deps`）。

![Python 环境 pip 选项卡](~/python/media/environments-pip-tab.png)

### <a name="intellisense-tab"></a>IntelliSense 选项卡

显示 IntelliSense 完成数据库的当前状态：

![Python 环境 IntelliSense 选项卡](~/python/media/environments-intellisense-tab.png)

数据库包含所有环境库的元数据，可提高 IntelliSense 速度并减少内存使用量。 Visual Studio 检测到新环境（或添加一个）时，它会通过分析库源文件，自动开始编译数据库 。 此过程可能会花一分钟到一小时不等或者更多时间，具体取决于安装的组件。 （例如，Anaconda 随附了许多库，需要花费一些时间来编译该数据库。）完成后，将获得 IntelliSense 的详细信息，并且在安装更多库之前，无需再次刷新数据库（使用“刷新 DB”按钮）。

其中数据尚未编译的库将使用 **!** 标记；如果环境的数据库未完成，则 **!** 也会出现在主环境列表中该环境的旁边。

## <a name="global-environments"></a>全局环境

全局（或系统范围内）环境可供计算机上的所有项目使用。 Visual Studio 通常会自动检测全局环境，可在 Python 环境窗口中查看这些环境。 否则，可如之前的[在 Visual Studio 中管理 Python 环境](#managing-python-environments-in-visual-studio)所述，手动添加一个环境。

Visual Studio 对所有新项目使用默认环境，用于执行、调试、检查语法、显示导入和成员完成情况以及任何需要环境的其他任务。 更改默认环境将影响尚未添加[特定于项目的环境](#project-specific-environments)的所有项目，如下所述。

## <a name="project-specific-environments"></a>特定于项目的环境

特定于项目的环境可确保项目始终在特定环境中运行，而不管默认全局环境。 例如，如果全局默认环境是 CPython，但项目需要 IronPython 和未在全局环境中安装的某些库，则必需一个特定于项目的环境。

项目环境在解决方案资源管理器中的 Python 环境节点下列出。 粗体显示的项当前处于活动状态，并将用于调试、导入和成员完成情况、语法检查以及任何需要的环境的其他任务：

![解决方案资源管理器中显示的项目环境](media/environments-project.png)

若要为项目激活其他环境，右键单击该环境，选择“激活环境”。

可通过右键单击“Python 环境”并选择“添加/删除 Python 环境...”，添加任何全局环境作为项目环境。 从显示的列表中，可以选择或取消选择项目中可用的项。

![“添加/删除 Python 环境”对话框](~/python/media/environments-add-remove.png)

在解决方案资源管理器中，还可以展开环境以显示其已安装的包（该环境处于活动状态时，可以导入并在代码中使用这些包）：

![解决方案资源管理器中某环境的 Python 包](~/python/media/environments-installed-packages.png)

若要安装新包，请右击该环境，选择“安装 Python 包...”，输入所需包的名称。 从 [Python 包索引 (PyPI)](https://pypi.python.org/pypi) 下载包（及其依赖项），还可以在其中搜索可用的包。 Visual Studio 的状态栏和输出窗口显示有关安装的信息。 若要卸载包，请右键单击它，选择“删除”。

> [!Note]
> 目前，核心 Python 开发团队正在开发 Python 的包管理支持。 显示的项未必总准确，且安装和卸载可能不可靠或不可用。 Visual Studio 使用 pip 程序包管理器（如果可用），并且需要时将下载并安装它。 Visual Studio 还可以使用 easy_install 程序包管理器。 也会显示使用 pip 或 easy_install 从命令行安装的包。

> [!Tip]
> 当包中包含用于 `*.pyd` 文件中本机组件的源代码时，Pip 无法安装包，这种情况很常见。 如果没有安装要求的 Visual Studio 版本，pip 将无法编译这些组件。 此情况下显示的错误消息是`error: Unable to find vcvarsall.bat.` `easy_install` 通常能够下载预编译二进制文件，且可从 [http://aka.ms/VCPython27](http://aka.ms/VCPython27) 下载较旧的 Python 版本适用的编译器。 有关详细信息，请参阅 Python 工具团队博客上的[How to deal with the pain of "unable to find vcvarsallbat"](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/)（如何处理“找不到 vcvarsallbat”问题）。


## <a name="virtual-environments"></a>虚拟环境

由于安装到全局环境中的包适用于使用它的所有项目，因此当两个项目需要不兼容的包或同一个包的不同版本时，可能会发生冲突。 若要避免此类冲突，Visual Studio 提供了创建*虚拟环境*的能力，这通常特定于项目。

像任何其他 Python 环境一样，虚拟环境由 Python 解释器、一个库和一组包组成。 不过在这种情况下，虚拟环境使用一个全局环境（前提是它支持虚拟环境）中的解释器和库，但其包独立并与全局环境和所有其他虚拟环境隔离。 这可再次避免发生冲突，并将虚拟环境的空间占用最大限度地减少到近似其包的大小。 

创建虚拟环境：

1. 在解决方案资源管理器中右键单击“Python 环境”并选择“添加虚拟环境...”，这将打开以下对话框：

    ![创建虚拟环境](~/python/media/environments-add-virtual-1.png)

1. 指定一个名称，在项目路径中创建虚拟环境，或指定一个完整路径，在其他位置创建。 （若要确保与其他工具的最大兼容性，请只在名称中使用字母和数字。）

1. 选择一个全局环境作为基础解释器，并单击“创建”。 如果 `pip` 和 `virtualenv`/`venv` 包不可用，将下载并安装它们。

    如果提供的路径是现有的虚拟环境，将检测到基础解释器且创建按钮将更改为“添加”：

    ![添加现有的虚拟环境](~/python/media/environments-add-virtual-2.png)

也可以通过在解决方案资源管理器中右键单击“Python 环境”，并选择“添加现有的虚拟环境...”来添加现有的虚拟环境。 Visual Studio 会使用环境的 `lib` 目录中的 `orig-prefix.txt` 文件自动检测基础解释器。

将虚拟环境添加到项目后，它将出现在“Python 环境”窗口中，可像激活任何其他环境一样激活它，且可以管理其包。 右键单击它并选择“删除”可删除对该环境的引用或删除该环境以及磁盘上它的所有文件（当然，不会删除基础解释器）。

请注意，虚拟环境的一个缺点是，它们包含硬编码文件路径，因此无法轻松地进行共享或传输到其他开发计算机上。 幸运的是，可以如下一节中所述使用 `requirements.txt` 文件。

## <a name="managing-required-packages"></a>管理所需的包

如果要使用生成系统与其他人共享项目或计划[将其发布到 Microsoft Azure](template-azure-cloud-service.md)，则需要指定它需要的外部包。 建议的方法是使用 [requirements.txt 文件](http://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org)，文件中包含将安装相关包所需的版本的 pip 命令列表。

从技术上讲，任何文件名都可用于跟踪要求（通过安装包时使用 `-r <full path to file>`，但 Visual Studio 提供针对 `requirements.txt` 的特定支持：

- 如果已加载包含 `requirements.txt` 的项目，且想要安装该文件列出的所有包，请右键单击该项目并选择“从 requirements.txt 安装”：

    ![从 requirements.txt 安装](~/python/media/environments-requirements-txt-install.png)

- 项目中安装有所有必要的包时，可以在解决方案资源管理器中右键单击该项目，并选择“生成 requirements.txt”来创建必要的文件。 如果文件已存在，系统将提示如何更新它：

    ![更新 requirements.txt 选项](~/python/media/environments-requirements-txt-replace.png)

    - “替换整个文件”将删除存在的所有项、注释和选项。
    - “刷新现有条目”将检测包的要求并更新版本说明符以匹配当前安装的版本。
    - “更新并添加项”将刷新找到的任何要求，并将所有其他包添加到文件末尾。

因为 `requirements.txt` 文件的目的是冻结项目的要求，因此所有已安装的包都采用精确的版本编写。 这可确保你轻松在其他计算机上重现环境。 即使采用一个版本范围（作为另一个包的依赖项）或使用安装程序而非 pip 安装了包，也会包含这些包。

添加新虚拟环境时，如果 ` requirements.txt` 文件存在，“”添加虚拟环境对话框将显示一个选项以自动安装包，从而可以轻松地在另一台计算机上重新创建环境：

![使用 requirements.txt 创建虚拟环境](~/python/media/environments-requirements-txt.png)

如果包不能通过 pip 安装，且它出现在 `requirements.txt` 文件中，则整个安装将失败。 在这种情况下，手动编辑文件以排除此包或使用 [pip 的选项](http://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format)来指包的可安装版本。 例如，你可能更喜欢使用 [`pip wheel`](http://pip.readthedocs.org/en/latest/reference/pip_wheel.html) 来编译依赖项，并向 `requirements.txt` 添加 `--find-links <path>` 选项：

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

# <a name="search-paths"></a>搜索路径

借助典型的 Python 用法，`PYTHONPATH` 环境变量（或 `IRONPYTHONPATH` 等）可为模块文件提供默认搜索路径。 也就是说，使用 `import <name>` 语句时，Python 首先会搜索其内置模块以查找匹配的名称，然后搜索包含正在运行的 Python 代码的文件夹，再搜索由适用的环境变量定义的“模块搜索路径”。 （请参阅核心 Python 文档中的[模块搜索路径](https://docs.python.org/2/tutorial/modules.html#the-module-search-path)和[环境变量](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH)。）

但 Visual Studio 将忽略搜索路径环境变量，即使已对整个系统进行了设置。 实际上，它被忽略的原因确切地说是*因为*对整个系统进行了此设置，且因此引发了某些无法自动得到答复的问题：引用的模块是否适用于 Python 2.7 或 Python 3.3？ 它们是否将替代标准库模块？ 开发人员是否注意到这一点，或者它是一个恶意的攻击尝试？

Visual Studio 中的 Python 支持提供一种方法，可直接在环境和项目中指定搜索路径。 从 Visual Studio 中调试或执行脚本时，它们将作为 `PYTHONPATH` 的值（或等效项）传递。 通过添加搜索路径，Visual Studio 将检查这些位置中的库并为它们构建 IntelliSense 数据库（这需要一些时间，具体取决于库的数量）。

若要添加搜索路径，请在解决方案资源管理器中右键单击“搜索路径”，选择“将文件夹添加到搜索路径...”，并选择要包括的文件夹。 此路径将用于与该项目关联的任何环境。

通过选择“将 Zip 存档添加到搜索路径的...”，还可将具有 `.zip` 或 `.egg` 扩展的文件添加为搜索路径。 与文件夹一样，将扫描这些文件的内容，并使其对 IntelliSense 可用。

> [!Note]
> 使用 Python 3.3 时，可将搜索路径添加到 Python 2.7 模块，但可能会看到错误是最后的结果。

如果定期使用相同的搜索路径，且内容不经常更改，则将其安装到 site-packages 文件夹会更高效。 它随后将进行分析并存储在 IntelliSense 数据库中、将始终与预期的环境关联且将不需要为每个项目添加搜索路径。

