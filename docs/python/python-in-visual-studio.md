---
title: "Visual Studio 中的 Python | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
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
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 9f888c27357a5e13fd5e1977bd51a200e928be64
ms.lasthandoff: 03/07/2017

---

# <a name="working-with-python-in-visual-studio"></a>在 Visual Studio 中使用 Python

Python 是一个受欢迎的编程语言，它可靠、灵活、易于学习、可在所有操作系统上免费使用，并且强大的开发人员社区和很多免费库都支持它。 Python 支持所有开发方式，包括 Web 应用程序、Web 服务、桌面应用、脚本编写和科学计算，许多高校人员、科学家、业余和专业开发人员都在使用 Python。 可以在 [python.org](https://www.python.org) 和 [Python for Beginners](https://www.python.org/about/gettingstarted/)（面向初学者的 Python）中了解有关该语言的详细信息。

Visual Studio 通过 Python 工作负载 (Visual Studio 2017) 和免费的针对 Visual Studio 的 Python 工具扩展（Visual Studio 2015 及更早版本），为 Python 提供[开源代码](https://github.com/Microsoft/ptvs)支持。 

请按照[安装说明](installation.md)设置 Python 工作负载，然后使用下方的链接详细了解与 Python 相关的功能，以及 Visual Studio 本身的功能。

| 功能 | 说明 | Visual Studio 常规文档 | 
| --- | --- | --- |
| [Visual Studio 项目系统](python-projects.md) | 隐式选取 Python 代码的文件夹结构，同时允许显式控制以便标识应用代码、测试代码、网页、JavaScript、生成脚本等等。 | [Visual Studio 中的解决方案和项目](../ide/solutions-and-projects-in-visual-studio.md) |
| [项目模板](python-projects.md#project-templates) | 快速创建用于控制台、Web、Azure、数据科学和其他类型项目的项目结构 | [Visual Studio 模板](../ide/creating-project-and-item-templates.md#visual-studio-templates) |
| 多个解释器支持 | 支持各种版本的 CPython 和 IronPython。 | 无 |
| IPython 支持 | 包括对内联图的 REPL 中的 IPython/Jupyter 的支持以及对.NET 和 Windows Presentation Foundation (WPF) 的支持。 | 无 |
| [多种多样的编辑、IntelliSense 和代码理解](code-editing.md) | 包括语法着色、跨所有代码和库的自动完成、[代码格式设置](code-formatting.md)、签名帮助、类视图、转到定义、查找所有引用、代码片段、[重构](code-refactoring.md)、[PyLint](code-pylint.md)等等。 | [在代码和文本编辑器中编写代码](../ide/writing-code-in-the-code-and-text-editor.md) |
| [交互窗口](interactive-repl.md) | 能够轻松突出显示代码的某一部分，然后将其发送到交互窗口，为 Python 提供快速的 REPL 体验。 | 无 |
| [功能完备的调试](debugging.md) | 无论有无 Visual Studio 项目，均可完成调试，包括可对现有可执行文件进行调试、[Python/C++ 混合模式调试](debugging-mixed-mode.md)、对 Windows/Linux/Mac 进行[远程调试](debugging-cross-platform-remote.md)、[对 Azure 进行远程调试](debugging-azure-remote.md)，以及在交互窗口中进行调试。 | [在 Visual Studio 中进行调试](../debugger/debugging-in-visual-studio.md) |
| [具有丰富报表的分析工具](profiling.md) | 了解应用程序中所用的时间，包括比较不同分析运行之间的性能差异。 | [分析工具](../profiling/profiling-tools.md)（并非所有 Visual Studio 分析功能都可用于 Python） |
| [单元测试工具](unit-testing.md) | 在 Visual Studio 测试资源管理器中发现、运行和管理测试，并且可轻松调试单元测试。 | [单元测试代码](../test/unit-test-your-code.md) |

Python 工作负载还包括[用于 Python 的 Azure SDK](azure-sdk-for-python.md)，它用于简化 Azure 服务的使用，并且提供面向 Windows、Mac OS X 和 Linux 的支持。

另请参阅 YouTube 上的[入门和进阶视频](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)系列，了解关于主要功能的概述。

[![Python 工具视频](media/video-general.png)](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)

## <a name="features-matrix"></a>功能矩阵

如[安装指南](installation.md)所述，可在以下版本的 Visual Studio 中安装 Python 支持：

- [Visual Studio 2017 预览版](https://www.visualstudio.com/vs/preview)
- [Visual Studio 2015（所有版本）](https://www.visualstudio.com/zh-cn/downloads/visual-studio-2015-downloads-vs)
- [Visual Studio 2013 Community Edition](https://www.visualstudio.com/zh-cn/products/visual-studio-community-vs.aspx)
- [Visual Studio Express 2013 for Web、Visual Studio Express 2013 Update 2 或更高版本](http://www.microsoft.com/en-us/download/details.aspx?id=40747)
- [用于桌面的 Visual Studio 2013 Express、Visual Studio Express 2013 Update 2 或更高版本](http://www.microsoft.com/en-us/download/details.aspx?id=40787)
- Visual Studio 2013（Pro 或更高版本）
- Visual Studio 2012（Pro 或更高版本）
- Visual Studio 2010 SP1（Pro 或更高版本；需要 .NET 4.5）

Visual Studio 各版本支持的功能：

| Python 支持 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 多个解释器管理 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 自动检测热门解释器 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 添加自定义解释器 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 虚拟环境 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Pip/易于安装 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| 项目系统 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 根据现有代码新建项目 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 显示所有文件 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 源代码管理 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Git 集成 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004;<sup>1</sup> | &#10007; |
<br/>

| 编辑 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 语法突出显示 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 自动完成 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 签名帮助 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 快速信息 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 对象浏览器/类视图 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 导航栏 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 转到定义 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 导航到 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 查找所有引用 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 自动缩进 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 代码格式设置 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 重构 - 重命名 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 重构 - 提取方法 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 重构 - 添加/删除导入 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| PyLint | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| 交互窗口 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 交互窗口 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 具有内联关系图的 IPython | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| 桌面 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 控制台/Windows 应用程序 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| IronPython WPF（带 XAML 设计器） | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| IronPython Windows 窗体 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Web | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Djano Web 项目 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Bottle Web 项目 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Flask Web 项目 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Generic Web 项目 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Azure | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 对网站的 Web 部署 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004;<sup>2</sup> |
| 对 Web 角色的 Web 部署 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| 对辅助角色的 Web 部署 | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| 在 Azure 仿真程序中运行 | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| 远程调试 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> | &#10007; |
| 服务器资源管理器附加 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> | &#10007; | &#10007; |
<br/>

| Django 模板 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 调试 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| 自动完成 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004; | &#10004; |
| CSS 和 JavaScript 的自动完成 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007; | &#10007; |
<br/>

| 调试 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 调试 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 不含项目进行调试 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 调试 - 附加到编辑 | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; |
| 混合模式调试 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| 远程调试（Windows、Mac OS X、Linux） | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; |
| 调试交互窗口 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| 分析 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 分析 | &#10004; | &#10004; | &#10004; | &#10007; | &#10007; | &#10004; | &#10004; | &#10004; |
<br/>

| 测试 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 测试资源管理器 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| 运行测试 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| 调试测试 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
<br/>

1. Visual Studio Tools for Git 扩展中提供了对 VS 2012 的 Git 支持，可从 [Visual Studio 库](http://visualstudiogallery.msdn.microsoft.com/abafc7d6-dcaa-40f4-8a5e-d6724bdb980c)中获得。

2. 部署到 Azure 网站需要[用于 .NET 2.1 - VS 2010 SP1 的 Azure SDK](http://go.microsoft.com/fwlink/?LinkId=313855)。  更高版本不支持 VS 2010。

3. 对 Azure Web 角色和辅助角色的支持需要[用于 .NET 2.3 - VS 2012 的 Azure SDK](http://go.microsoft.com/fwlink/?LinkId=323511) 或更高版本。

4. 对 Azure Web 角色和辅助角色的支持需要[用于 .NET 2.3 - VS 2013 的 Azure SDK](http://go.microsoft.com/fwlink/?LinkId=323510) 或更高版本。

5. Visual Studio 2013 中的 Django 模板编辑器具有一些已知问题，可通过安装 Update 2 解决。

6. 需要 Windows 8 或更高版本。 Visual Studio 2013 Express for Web 没有“附加到进程”对话框，但 Azure 网站远程调试仍然可能在服务器资源管理器中使用附加调试器 (Python) 命令。 这需要[用于.NET 2.3 - VS 2013 的 Azure SDK](http://go.microsoft.com/fwlink/?LinkId=323510) 或更高版本。

7. 需要 Windows 8 或更高版本。 使用服务器资源管理器中的附加调试器 (Python) 命令需要[用于 .NET 2.3 - VS 2013 的 Azure SDK](http://go.microsoft.com/fwlink/?LinkId=323510) 或更高版本。

8. 需要 Windows 8 或更高版本。

## <a name="additional-resources"></a>其他资源

- [使用 PyKinect 通过 Python 编写 Kinect 游戏](https://github.com/Microsoft/PTVS/wiki/PyKinect) (GitHub wiki)
- [IIS 和 Python 之间 WFastCGI 桥](https://pypi.python.org/pypi/wfastcgi) (python.org)
