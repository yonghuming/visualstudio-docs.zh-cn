---
title: "开发人员测试工具、方案和功能 | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unit testing, create unit tests
ms.assetid: 9DE41406-8D39-427E-99D9-987E99103B73
caps.latest.revision: 56
ms.author: douge
manager: douge
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
ms.sourcegitcommit: c559290c8e88c8b4e37feabc7014188fad15434d
ms.openlocfilehash: b36882588281fc95ff4814c148cd428d09196fa1
ms.contentlocale: zh-cn
ms.lasthandoff: 06/08/2017

---
# <a name="developer-testing-tools-scenarios-and-capabilities"></a>开发人员测试工具、方案和功能

使用单元测试维持代码正常运行。 Visual Studio 提供各种功能强大的工具和技术供开发人员在测试应用程序时使用：

**方案和功能：**

* [通过 IntelliTest 避免回归并实现代码覆盖率](#intellitest)
* [通过编码的 UI 和 Selenium 进行用户界面测试](#ui-testing)
* [使用 Visual Studio 代码覆盖率进行有效的单元测试](#unit-testing)
* [通过使用高性能测试资源管理器的任何框架进行单元测试](#test-explorer)
* [单元测试入门](getting-started-with-unit-testing.md)

<a name="intellitest"></a>
## <a name="avoid-regressions-and-achieve-code-coverage-with-intellitest"></a>通过 IntelliTest 避免回归并实现代码覆盖率

在传统的单元测试套件中，每个测试用例都表示一个典型的使用方案，而断言则体现输入和输出之间的关系。  此类方案验证几种也许就已足够，但经验丰富的开发人员知道当正确但未经测试的输入引发错误响应时，即使在经充分测试的代码中也可能潜伏有 bug。

通过 IntelliTest 增加覆盖率，避免回归。
IntelliTest 大大减少了创建和维护新代码或现有代码的单元测试的工作量。 

![操作中的 IntelliTest](media/devtest-intellitest.png)

* [Visual Studio 的 IntelliTest 简介](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20IntelliTest%20with%20Visual%20Studio%20Enterprise%202015.docx)
* [IntelliTest - One Test to rule them all ](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/05/intellitest-one-test-to-rule-them-all.aspx)（IntelliTest - 一个测试掌控所有情况）
* [IntelliTest 视频](https://channel9.msdn.com/Series/Test-Tools-in-Visual-Studio)
* [IntelliTest 入门](generate-unit-tests-for-your-code-with-intellitest.md)
* [IntelliTest 参考手册](intellitest-manual/index.md)

<a name="ui-testing"></a>
## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>通过编码的 UI 和 Selenium 进行用户界面测试

通过最适用的或社区批准的 UI 测试来测试用户界面 (UI)。
编码的 UI 测试提供了一种方法来创建完全自动化的测试，用来验证应用程序用户界面的功能和行为。
它们可在各种技术（包括基于 XAML 的 Windows 应用商店应用、浏览器应用和 SharePoint 应用）中自动进行 UI 测试。

无论选择最适用的编码 UI 测试还是使用 Selenium 进行的基于泛型浏览器的 UI 测试，Visual Studio 均提供所有所需的工具。 

![使用编码的 UI 进行 UI 测试](media/devtest-codeduitest.png)

* [使用 UI 自动化来测试代码](use-ui-automation-to-test-your-code.md)
* [创建、编辑和维护编码的 UI 测试入门](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [使用编码的 UI 测试来测试 Windows 应用商店应用](test-windows-store-8-1-apps-with-coded-ui-tests.md)
* [使用编码的 UI 测试来测试 Windows Phone 应用](test-windows-phone-8-1-apps-with-coded-ui-tests.md)
* [使用编码的 UI 测试来测试 SharePoint 应用程序](testing-sharepoint-2010-applications-with-coded-ui-tests.md)
* [使用 Visual Studio Enterprise（实验室）进行编码的 UI 测试简介](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20Coded%20UI%20Tests%20with%20Visual%20Studio%20Enterprise%202015.docx)

<a name="unit-testing"></a>
## <a name="effective-unit-testing-with-visual-studio-code-coverage"></a>使用 Visual Studio 代码覆盖率进行有效的单元测试

若要确定正在由编码的测试（例如单元测试）实际进行测试的项目代码的比例，则可以使用 Visual Studio 的代码覆盖率功能。 若要有效防止 Bug，测试应作用于或“覆盖”大部分代码。

可将代码覆盖率分析应用于托管 (CLI) 和非托管（本机）代码。

代码覆盖率是使用测试资源管理器运行测试方法时的一个选项。 结果表将显示在各个程序集、类和方法中运行的代码的百分比。 此外，源编辑器将显示已测试的代码。

![使用 Visual Studio Team Services 和 Team Foundation Server 进行测试](media/devtest-codecoverage.png)

* [使用代码覆盖率确定所测试的代码量](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [使用 Visual Studio（实验室）进行单元测试、代码覆盖率分析和代码克隆分析](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [自定义代码覆盖率分析](customizing-code-coverage-analysis.md)

<a name="test-explorer"></a>
## <a name="unit-testing-with-any-framework-using-the-high-performance-test-explorer"></a>通过使用高性能测试资源管理器的任何框架进行单元测试

测试资源管理器帮助开发人员创建、管理单元测试并从中获得最大的好处。

![Visual Studio 测试资源管理器](media/devtest-testexplorer.png)

* [单元测试入门](unit-test-your-code.md)
* [使用测试资源管理器运行单元测试](run-unit-tests-with-test-explorer.md)
* [编写 C/C++ 单元测试](writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)
* [安装第三方单元测试框架](install-third-party-unit-test-frameworks.md)

Visual Studio 也可扩展，并支持第三方单元测试适配器，如 NUnit 和 xUnit.net。 此外，通过帮助识别在语义上类似的代码块（这可能是常见 bug 修复或重构的备选项），代码克隆功能还同时可以获得高质量的软件。

![第三方测试集成](media/devtest-thirdparty.png)

## <a name="also-see"></a>另请参阅

* [单元测试入门](getting-started-with-unit-testing.md)
* [Speeding up Unit Test Execution in Team Foundation Server](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/30/speeding-up-test-execution-in-tfs.aspx)（在 Team Foundation Server 中加快单元测试执行）
* [并行和区分上下文的单元测试执行](https://blogs.msdn.microsoft.com/visualstudioalm/2016/02/08/parallel-and-context-sensitive-test-execution-with-visual-studio-2015-update-1/)
* [使用 Visual Studio（实验室）进行单元测试、代码覆盖率分析和代码克隆分析](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)

