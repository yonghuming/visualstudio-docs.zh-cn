---
title: "Visual Studio 中的 Live Unit Testing | Microsoft Docs"
ms.date: 2017-03-07
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
ms.assetid: 5b51fb96-94f4-4926-92b9-262156c05b85
author: rpetrusha
ms.author: ronpet
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
ms.sourcegitcommit: edb6c75d35f89df363a07eb24ba31e203bc6672e
ms.openlocfilehash: 30261d8b75029bac15c9ab881d9f43c1a717d8cd
ms.lasthandoff: 03/15/2017

---

# <a name="live-unit-testing-with-visual-studio-2017"></a>使用 Visual Studio 2017 进行实施单元测试

在你开发应用程序时，Live Unit Testing 将在后台自动运行任何受影响的单元测试并在 Visual Studio IDE 中实时显示结果和代码覆盖率。 在你修改代码时，Live Unit Testing 可提供关于更改如何影响现有测试和新增代码是否会被一个或多个现存测试覆盖的反馈。 这可在你进行 bug 修复或添加新功能时，温馨地提示你编写单元测试。

> [!NOTE]
> Live Unit Testing 适用于面向企业版 Visual Studio 2017 中的 .NET Framework 的 C# 和 Visual Basic 项目。 目前，不适用于 .NET Core。

## <a name="supported-test-frameworks"></a>受支持的测试框架

Live Unit Testing 适用于下表中列出的三个常用的单元测试框架。 表中还列出了其适配器和框架支持的最低版本。 单元测试框架都可从 NuGet.org 获得。
 
<table> 
<tr>
   <th>测试框架</th>
   <th>Visual Studio 适配器最低版本</th>
   <th>Framework 最低版本</th>
</tr>
<tr>
   <td>xUnit.net</td>
   <td> xunit.runner.visualstudio 版本 2.2.0-beta3-build1187</td>
   <td>xunit 2.0</td> 
</tr>
<tr>
   <td>NUnit</td>
   <td>NUnit3TestAdapter 版本 3.5.1</td>  
   <td>NUnit 版本 3.5.0</td>
</tr>
<tr>
   <td>MSTest</td>
   <td>MSTest.TestAdapter 1.1.4-预览版</td>
   <td>MSTest.TestFramework 1.0.5-预览版</td>
</tr>
</table>

如果你具有来自现有项目的旧适配器和测试框架引用，请务必将其删除。 （如果使用 MSTest，请确保删除对 `Microsoft.VisualStudio.QualityTools.UnitTestFramework` 的引用。）如果 Live Unit Testing 无法正常运行，请添加新的。 

在某些情况下，可能需要显式还原解决方案中项目引用的 NuGet 包，以便 Live Unit Testing 可正常运行。 你可以先通过显式生成解决方案（从顶级 Visual Studio 菜单中选择“生成”>“重新生成解决方案”）或通过还原解决方案中的包（右键单击解决方案并选择“还原 NuGet 包”）实现此操作，然后再启用 Living Unit Testing。 

#    <a name="configuring-live-unit-testing"></a>配置 Live Unit Testing

可以通过从顶级 Visual Studio 菜单中选择“工具”>“选项”，然后在“选项”对话框左窗格中选择“Live Unit Testing”来配置 Live Unit Testing。 下图显示对话框中可用的 Live Unit Testing 配置选项。

  ![Image](./media/lut-options.png)

可配置选项包括：

- 打开解决方案时 Live Unit Testing 是否自动运行。
- 生成或调试解决方案或系统电量低于指定阈值时是否暂停 Live Unit Testing。
- 测试用例超时之前的时间间隔；隔默认值为 30 秒。 
- Live Unit Testing 创建的测试进程数。 
- 写入 Live Unit Testing“输出”窗口的信息级别。 选项包括无日志记录（无）、仅限错误消息（错误）、错误和信息性消息（默认值为信息）或所有详细信息（详细）。

还可以通过向名为 `VS_UTE_DIAGNOSTICS` 的用户级环境变量分配值“1”并重启 Visual Studio 在 Live Unit Testing“输出”窗口显示详细输出。 

若要捕获从 Live Unit Testing 到文件的详细 MSBuild 日志消息，请将 `LiveUnitTesting_BuildLog` 用户级环境变量设为该文件的名称以包含日志。

## <a name="starting-pausing-and-stopping-live-unit-testing"></a>启动、暂停和停止 Live Unit Testing

通过从顶级 Visual Studio 菜单中依次选择“测试”、“Live Unit Testing”和“启动”来启用 Live Unit Testing。 启用 Live Unit Testing 后，“Live Unit Testing”菜单上的可用选项从单项的“开始”变为“暂停”、“停止”和“重启”。

在任何时候，都可以临时暂停或完全停止 Live Unit Testing。 例如，当你正在重构且知道测试将停止一段时间时，你可能想要执行此操作。 三个菜单选项为：

- **暂停**，用于临时挂起 Live Unit Testing。 
    暂停 Live Unit Testing 后，覆盖率可视化效果不会出现在编辑器中，但会保留所有已收集的数据。 若要恢复 Live Unit Testing，请从 Live Unit Testing 菜单中选择“继续”。 Live Unit Testing 将执行必要工作，以便与其暂停时所做的所有编辑保持同步，并相应地更新字形。 
- **停止**，用于完全停止 Live Unit Testing。 Live Unit Testing 将放弃所有已收集的数据
- **重启**，相当于从“Live Unit Testing”菜单中选择“停止”，然后选择“开始”。

##    <a name="viewing-coverage-visualization-in-the-editor-as-you-type"></a>在编辑器中查看键入时的覆盖率可视化效果

一旦启用，Live Unit Testing 将在 Visual Studio 编辑器中更新每行代码，以显示正在编写的代码是否由单元测试覆盖以及覆盖这些代码的测试是否通过。  下图显示测试通过和失败的代码行，以及测试未覆盖的代码行。 绿色“✓”修饰的行表示仅由通过测试覆盖，红色“🞩”修饰的行表示由一项或多项失败测试覆盖，蓝色“”修饰的行表示未被任何测试覆盖。

  ![Image](./media/lut-codewindow.png)

当你在代码编辑器中修改代码后，将立即更新 Live Unit Testing 覆盖率可视化效果。 处理编辑时，可视化效果将变化，通过在通过、失败和未覆盖符号下方添加圆形计时器图像来指示数据非最新，如下图所示。

  ![Image](./media/lut-codeupdating.png)
 
## <a name="getting-information-on-successful-or-failed-tests"></a>获取关于成功或失败测试的信息

将鼠标悬停在代码窗口中的成功或失败符号上，可以看到符合此条件的测试数目。 如果单击该符号，可以查看各个测试的状态，如下图所示。
 
  ![Image](./media/lut-failedinfo.png) 

当鼠标悬停于工具提示中的失败测试时，它将展开以提供关于失败的详细信息，如下图所示。 如果单击工具提示中的未通过测试，你可以直接导航到它。

  ![Image](./media/lut-failedmsg.png) 

## <a name="diagnosing-and-correcting-test-failures"></a>诊断和更正测试失败

根据失败测试，你可以轻松对产品代码进行调试、进行编辑，并继续开发应用程序。 由于 Live Unit Testing 在后台运行，无需在调试、编辑和继续循环期间停止和重启 Live Unit Testing。

例如，上图所示测试失败是由于在测试方法中错误地认为非字母字符在传递到 [Char.IsLower](xref:System.Char.IsLower(System.Char)) 方法时返回 `true`。 一旦更正测试方法，我们将发现所有测试均通过。 我们执行此操作时，不需要暂停或停止 Live Unit Testing。

## <a name="live-unit-testing-and-test-explorer"></a>Live Unit Testing 和测试资源管理器

通常，**测试资源管理器**具有可供运行、调试和分析测试结果的界面。 Live Unit Testing 与**测试资源管理器**集成。 当 Live Unit Testing 未启用或已停止时，**测试资源管理器**将显示上次运行测试时的单元测试状态。 源代码更改需要重新运行测试。 与此相反，启用 Live Unit Testing 后，**测试资源管理器**中的单元测试状态将立即更新。 不再需要显式运行单元测试。 

但是，Live Unit Testing 自动运行和更新测试结果以及从**测试资源管理器**显式运行测试之间存在一些差异。 其中包括:

- 从测试资源管理器窗口运行或调试测试将运行常规二进制文件，而 Live Unit Testing 运行已检测二进制文件。 
- Live Unit Testing 不会创建新的应用程序域来运行测试，而是从默认域运行测试。 从**测试资源管理器**窗口运行的测试确实会创建新的应用程序域。
- Live Unit Testing 按顺序运行每个测试程序集中的测试。 如果从“测试资源管理器”窗口运行多个测试，且已选择“并行运行测试”按钮，则测试将并行运行。

## <a name="including-and-excluding-test-projects-and-test-methods"></a>包括和排除测试项目和测试方法

对于含多个测试项目的解决方案，可以控制参与 Live Unit Testing 的项目和项目中的单个方法。 

例如，如果你的解决方法含数百个测试项目，你可以选择一组目标测试项目来参与 Live Unit Testing。 若要在单元测试中选择单个项目，请在启动 Live Unit Testing 后执行以下操作：

1.    在解决方案资源管理器中单击解决方案并依次选择“实时测试”、“排除”以排除整个解决方案。
2.    右键单击想要包括在测试中的每个测试项目，然后依次选择“实时测试”“包括”。
 
使用代码编辑器窗口包含或排除单个测试方法。 在代码编辑器窗口中单击测试方法的签名，然后依次选择“实时测试”、“包括”或“实时测试”“排除”。 

或者，还可以应用 [<ExcludeFromCodeCoverage>](https://msdn.microsoft.com/library/system.diagnostics.codeanalysis.excludefromcodecoverageattribute.aspx) 属性以编程方式排除方法、类或结构报告其在 Live Unit Testing 中的覆盖率。

关闭或重新打开解决方案时，Live Unit Testing 将包括/排除状态另存为用户设置并将其记住。 

## <a name="see-also"></a>另请参阅

[Live Unit Testing 博客](https://go.microsoft.com/fwlink/?linkid=842514)   
[Live Unit Testing 常见问题解答](live-unit-testing-faq.md)    
[第 9 频道视频：Visual Studio 2017 中的实时单元测试](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)


