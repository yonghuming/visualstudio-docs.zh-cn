---
title: "升级 Visual Studio 2010 单元测试项目 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1502b51-d6db-4894-9fbf-4a5723e4bb1a
caps.latest.revision: 8
ms.author: douge
manager: douge
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: d6550f2aa1aab249eda569ff84ddf4dcf488aa18
ms.contentlocale: zh-cn
ms.lasthandoff: 05/13/2017

---
# <a name="upgrade-visual-studio-2010-unit-test-projects"></a>升级 Visual Studio 2010 单元测试项目
[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 包括与 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 测试项目的测试项目兼容性。 例如，使用 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 创建的测试项目可通过 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 打开，而无需任何升级。 因此，团队可以同时使用 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 和 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 处理同一测试项目。 有关详细信息，请参阅[从 Visual Studio 2010 升级测试](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52)。  
  
 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 引入了多项单元测试更改。 由于这些更改，了解 Visual Studio 早期版本和 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 之间的兼容性问题变得十分重要。 在这些对单元测试的更改中，一个重要的变化为 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 包括了不止一个测试项目模板，其中包括单元测试项目模板。 新单元测试项目模板中添加了新的单元测试。 单元测试也可以包含在另一个新的测试项目模板中，名为编码的 UI 测试项目模板。 有关新测试项目模板的详细信息，请参阅[从 Visual Studio 的早期版本升级测试](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52)。 默认情况下，新单元测试项目不再包括一个测试设置文件。 通过排除测试设置文件，单元测试的性能将得到提升。 至于兼容性，您仍然可以使用通过 Visual Studio 2010 创建的现有测试项目。 但是，出于性能原因，我们建议除非特别需要测试设置文件，否则请移除与测试项目关联的测试设置文件。 例如，如果在分布式环境中运行单元测试，或需要收集特定的诊断数据，则您可以选择保留测试设置文件。 在使用新的单元测试项目模板或编码的 UI 测试项目模板时，如果您有类似需要，也可以手动向其添加测试设置文件。  
  
> [!NOTE]
>  [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 测试项目中的现有单元测试可在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 和 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 之间无缝运行。 在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中打开包含单元测试的 Visual Studio 2010 测试项目时，不会对测试项目文件做任何更改，反之亦然。  
  
> [!CAUTION]
>  Visual Studio 2010 不能打开面向 11.0 工具集的 C++/CLI 项目，即使用 Visual Studio 2012 创建的项目。 此限制适用于所有 C++/CLI 项目，而不仅仅是 C++/CLI 单元测试项目。  
  
> [!NOTE]
>  可以从命令行使用 vstest.console.exe 命令运行新的单元测试。 有关使用 vstest.console.exe 的详细信息，请参阅 [VSTest.Console.exe 命令行选项](/devops-test-docs/test/vstest-console-exe-command-line-options)，或使用帮助开关运行命令：**vstest.console.exe /?**。 使用 MStest.exe 可以继续运行现有的单元测试。 有关详细信息，请参阅[使用 MSTest 从命令行运行自动测试](/devops-test-docs/test/run-automated-tests-from-the-command-line-using-mstest)和 [MSTest.exe 命令行选项](/devops-test-docs/test/mstest-exe-command-line-options)。  
  
 另一个重要的变化为新的测试资源管理器。 在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中，您在 Visual Studio 早期版本中可能比较熟悉的一些测试窗口已遭弃用，例如“测试视图”窗口。 测试资源管理器旨在为开发人员和团队提供更好的支持，帮助其将单元测试纳入软件开发实践中。 有关详细信息，请参阅[使用测试资源管理器运行单元测试](../test/run-unit-tests-with-test-explorer.md)。  
  
## <a name="compatibility-issues-between-visual-studio-2010-sp1-and-visual-studio-2012"></a>Visual Studio 2010 SP1 和 Visual Studio 2012 之间的兼容性问题  
 以下是一些在 Visual Studio 2010 SP1 和 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 之间迁移单元测试时需要注意的问题：  
  
|单元测试功能|问题|解决方案|  
|-----------------------------|-----------|--------------|  
|测试列表（.vsmdi 文件）在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中已遭弃用。|你无法再创建新的测试列表（.vsmdi 文件），也无法通过 Visual Studio 运行测试列表。 **提示：**测试类别比 Microsoft Visual Studio 早期版本中的测试列表功能具有更大的灵活性。 可以在测试类别中使用逻辑运算符，从而运行来自多个类别的测试，或将运行的测试仅限于属于多个类别的测试。 此外，在创建测试方法时很容易添加测试类别，创建测试方法后也无需维护测试列表。 通过使用测试类别，你无需签入和签出用于维护测试列表的“\<解决方案名称>.vsmdi”文件。 有关详细信息，请参阅[定义对测试进行分组的测试类别](/devops-test-docs/test/defining-test-categories-to-group-your-tests)。|-   为了继续兼容采用测试列表的现有测试项目，你仍可以使用 Visual Studio 编辑 .vsmdi 文件。<br />-   尽管无法使用 Visual Studio 运行迁移的测试列表，但仍可从命令行使用 mstest.exe 命令运行列表。 有关详细信息，请参阅[如何：从命令行使用 MSTest 运行自动测试](/devops-test-docs/test/run-automated-tests-from-the-command-line-using-mstest)<br />-   如果你在生成定义中使用的是测试列表，则可以继续使用它。 有关详细信息，请参阅[如何：在生成应用程序之后配置和运行计划的测试](http://msdn.microsoft.com/en-us/32acfeb1-b1aa-4afb-8cfe-cc209e6183fd)和[在生成过程中运行测试](http://msdn.microsoft.com/Library/d05743a1-c5cf-447e-bed9-bed3cb595e38)。|  
|专用访问器在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中已遭弃用。<br /><br /> 在 Visual Studio 的早期版本中，您可以使用 Publicize 指定内部应用程序编程接口 (API)，并创建可在测试中调用的公共对应 API，后者将调用产品的内部 API。 然后，您可以使用代码创建测试存根，并在此存根内生成代码片段。|您无法再创建专用访问器。|<ul><li>Visual Studio 2010 测试项目将在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中编译和运行。 生成版本将包含输出警告。</li><li>如果仍需要测试内部 API，则可以使用以下选项：<br /><br /> <ul><li>使用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> 类可帮助访问代码中的内部和私有 API。 这可以在 Microsoft.VisualStudio.QualityTools.UnitTestFramework.dll 程序集中找到。</li><li>创建能够反射代码以访问内部或私有 API 的反射框架。</li><li>如果您尝试访问的代码是内部代码，则可以使用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 访问 API，以便测试代码能够访问内部 API。</li></ul></li></ul>|  
|消除测试影响|||  
|通过测试资源管理器中的 TRX 日志共享运行结果。||你仍可以从命令行和 Team Build 获取 TRX 日志。|  
  
## <a name="see-also"></a>另请参阅  
 [移植、迁移和升级 Visual Studio 项目](../porting/port-migrate-and-upgrade-visual-studio-projects.md)   
 [单元测试代码](../test/unit-test-your-code.md)   
 [从 Visual Studio 的早期版本升级测试](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52)   
 [从 Visual Studio 2010 升级编码的 UI 测试](../test/upgrading-coded-ui-tests-from-visual-studio-2010.md)

