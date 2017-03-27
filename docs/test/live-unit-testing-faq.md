---
title: "Live Unit Testing 常见问题解答 | Microsoft Docs"
ms.date: 2017-03-13
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing FAQ
ms.assetid: 61baf3bb-646f-4c5a-b7c0-a6bdff68f21c
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
ms.openlocfilehash: 1c200c5f9dd295fff54784e7ebe20cea2ce99cf1
ms.lasthandoff: 03/15/2017

---
# <a name="live-unit-testing-frequently-asked-questions"></a>Live Unit Testing 常见问题解答

## <a name="does-live-unit-testing-work-with-net-core"></a>Live Unit Testing 是否适用于 .NET Core？  

**答：**

Live Unit Testing 当前不适用于 .NET Core。 我们正为将来添加此支持而努力。 

## <a name="why-doesnt-live-unit-testing-work-when-i-turn-it-on"></a>启用 Live Unit Testing 后，为什么它不工作？ 

**答：** 

**输出窗口**（选中 Live Unit Testing 下拉列表时）应会告知 Live Unit Testing 不工作的原因。 Live Unit Testing 可能由于以下原因之一而不工作： 

- 如果未还原解决方案中项目引用的 NuGet 包，Live Unit Testing 不工作。 启用 Live Unit Testing 前，对解决方案执行显式生成或还原解决方案中的 NuGet 包应可解决此问题。 

- 如果在项目中使用基于 MSTest 的测试，请确保删除对 `Microsoft.VisualStudio.QualityTools.UnitTestFramework` 的引用，并添加对最新 MSTest NuGet 包 `MSTest.TestAdapter`（要求最低版本为 1.1.4-预览版）和 `MSTest.TestFramework`（要求最低版本为 1.0.5-预览版）的引用。 有关详细信息，请参阅[使用 Visual Studio 2017 Enterprise Edition 中的 Live Unit Testing](live-unit-testing.md#supported-test-frameworks) 主题的“支持的测试框架”部分。
 
- 解决方案中至少一个项目应有针对 xUnit、NUnit 或 MSTest 测试框架的 NuGet 引用或直接引用。 此项目还应引用相应的 Visual Studio 测试适配器 NuGet 包。 还可以通过 `.runsettings` 文件引用 Visual Studio 测试适配器。 `.runsettings` 文件必须包含如下条目： 

   ```xml
    <RunSettings> 
       <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
       </RunConfiguration> 
    </RunSettings> 
   ``` 

## <a name="can-i-customize-my-live-unit-testing-builds"></a>是否可以自定义 Live Unit Testing 生成？ 

**答：**

如果解决方案需要为检测 (Live Unit Testing) 而生成的自定义步骤，而非检测的“常规”生成不需要，可向项目或目标文件添加代码，检查 `BuildingForLiveUnitTesting` 属性并执行自定义生成前/后步骤。 还可以选择删除特定的生成步骤（如发布或生成包），或将生成步骤（如复制先决条件）添加到基于此项目属性的 Live Unit Testing 生成。 这不会以任何方式更改常规生成，只会影响 Live Unit Testing 生成。 

例如，常规生成过程中可能有生成 NuGet 包的目标。 可能不需要每次编辑后都生成 NuGet 包。 因此，可以通过执行以下操作在 Live Unit Testing 生成中禁用该目标：   

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'"> 
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/> 
</Target> 
```

## <a name="error-messages-with-ltoutputpathgt-or-ltoutdirgt"></a>&lt;OutputPath&gt;或&lt;OutDir&gt; 错误消息

**Live Unit Testing 尝试生成解决方案时为什么出现了以下错误：“….似乎无条件地设置 `<OutputPath>` 或 `<OutDir>`。Live Unit Testing 将不会从输出程序集执行测试”？**

**答：**

如果解决方案的生成过程无条件地替代 `<OutputPath>` 或 `<OutDir>`，使其不是 `<BaseOutputPath>` 的子目录，则可能会出现这种情况。 在这种情况下，Live Unit Testing 不会工作，因为它也会替代这些内容以确保将生成项目拖放到 `<BaseOutputPath>` 下的文件夹。 如果在一个常规生成中，必须替代要放入生成项目的位置，请基于 `<BaseOutputPath>` 有条件地替代 `<OutputPath>`。 

例如，如果生成过程如下所示替代 `<OutputPath>`： 

```xml 
<Project> 
  <PropertyGroup> 
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath> 
  </PropertyGroup> 
</Project> 
```

然后使用以下代码替换它： 

```xml 
<Project> 
  <PropertyGroup> 
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath> 
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath> 
  </PropertyGroup> 
</Project> 
```
 
这可确保 `<OutputPath>` 位于 `<BaseOutputPath>` 文件夹中。 
 
请勿直接在生成过程中替代 `<OutDir>`；请转而替代 `<OutputPath>` 以将生成项目放置到特定位置。
  
## <a name="setting-the-location-of-live-unit-testing-build-artifacts"></a>设置 Live Unit Testing 生成项目的位置

**我想要将 Live Unit Testing 生成的项目转到特定位置，而不是 `.vs` 文件夹下的默认位置。可如何进行更改？**
 
**答：**

将 `LiveUnitTesting_BuildRoot` 用户级环境变量设置为想要放置 Live Unit Testing 生成项目的路径。  

## <a name="how-is-running-tests-from-test-explorer-window-different-from-running-tests-in-live-unit-testing"></a>从测试资源管理器窗口运行测试与在 Live Unit Testing 中运行测试有何不同之处？ 

**答：**

有几个区别： 

- 从测试资源管理器窗口运行或调试测试将运行常规二进制文件，而 Live Unit Testing 运行已检测二进制文件。 如果想要调试已检测的二进制文件，可在测试方法中添加 [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) 方法调用，这会导致每当执行该方法时（包括其由 Live Unit Testing 执行时）都启动调试器，然后可附加和调试已检测的二进制文件。 但我们希望检测对于大多数用户方案是透明的，不需要调试要检测的二进制文件。 

- Live Unit Testing 不会创建新的应用程序域来运行测试，但从测试资源管理器窗口运行的测试确实会创建新的应用程序域。 

- Live Unit Testing 按顺序运行每个测试程序集中的测试，但如果从测试资源管理器窗口运行多个测试，并选择“并行运行测试”按钮，它们将并行运行。 

- Live Unit Testing 中测试的发现和执行使用 `TestPlatform` 版本 2，而测试资源管理器窗口使用版本 1。 但在大多数情况下，应该不会注意到有差异。  

- 测试资源管理器当前默认以单线程单元 (STA) 运行测试，而 Live Unit Testing 以多线程单元 (MTA) 运行测试。 若要在 Live Unit Testing 中以 STA 实运行 MSTest 测试，请 `MSTest.STAExtensions 1.0.3-beta` NuGet 包中可找到的 `<STATestMethod>` 或 `<STATestClass>` 属性修饰测试方法或所包含的类。 对于 NUnit，请使用 `<RequiresThread(ApartmentState.STA)>` 属性修饰测试方法，对于 xUnit，则使用 `<STAFact>` 属性。
 
## <a name="how-do-i-exclude-tests-from-participating-in-live-unit-testing"></a>如何排除测试参与 Live Unit Testing？

**答：**

请参阅[使用 Visual Studio 2017 Enterprise Edition 中的实时单元测试](live-unit-testing.md#including-and-excluding-test-projects-and-test-methods)主题的“包括和排除测试项目和测试方法”部分，了解特定于用户的设置。 想要针对特定的编辑会话运行一组特定的测试或者保留个人偏好设置时，这非常有用。
  
对于特定于解决方案的设置，可采用编程方式应用 <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> 属性，排除方法、属性、类或结构由 Live Unit Testing 进行检测。 此外，还可以在项目文件中将 `<ExcludeFromCodeCoverage>` 属性设置为 `true`，排除整个项目进行检测。 Live Unit Testing 仍将运行未经检测的测试，但其范围将不进行可视化。

还可以检查是否在当前应用程序域中加载 `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` 并禁用基于其的测试。 例如，可使用 xUnit 执行诸如以下所示的操作：

```cs
[ExcludeFromCodeCoverage]
public class SkipLiveFactAttribute : FactAttribute
{
   private static bool s_lutRuntimeLoaded = AppDomain.CurrentDomain.GetAssemblies().Any(a => a.GetName().Name == 
                                            "Microsoft.CodeAnalysis.LiveUnitTesting.Runtime");
   public override string Skip => s_lutRuntimeLoaded ? "Test excluded from Live Unit Testing" : "";
}

public class Class1
{
   [SkipLiveFact]
   public void F()
   {
      Assert.True(true);
   }
}
```

## <a name="why-are-win32-pe-headers-different-in-instrumented-assemblies-built-by-live-unit-testing"></a>为什么 Win32 PE 标头在 Live Unit testing 生成的已检测程序集中不同？ 

**答：**

存在一个已知的 bug，它可能会导致 Live Unit Testing 无法嵌入以下 Win32 PE 标头数据： 

- 文件版本（由代码中的 @System.Reflection.AssemblyFileVersionAttribute 指定）。 

- Win32 图标（由命令行上的 `/win32icon:` 指定）。 

- Win32 清单（由命令行上的 `/win32manifest:` 指定）。 

由 Live Unit Testing 执行依赖于这些值的测试时，测试可能会失败。

## <a name="why-does-live-unit-testing-keep-building-my-solution-all-the-time-even-if-i-am-not-making-any-edits"></a>为什么即使我没有进行任何编辑，Live Unit Testing 仍一直生成我的解决方案？ 

**答：**

如果解决方案的生成过程生成的源代码属于解决方案本身，并且生成目标文件没有指定的相应输入和输出，则可能会发生这种情况。 应给定目标一个输入和输出列表，使 MSBuild 可执行适当的最新检查，并确定是否需要新的生成。 

Live Unit Testing 只要检测到源文件已更改，就会启动一个生成。 由于解决方案的生成过程生成源文件，Live Unit Testing 将进入一个无限的生成循环。 但如果 Live Unit Testing 启动第二次生成时（从上一生成中检测到新生成的源代码文件后）检查了目标的输入和输出，它将中断该循环，因为输入和输出检查将表明所有内容都为最新。   

## <a name="how-does-live-unit-testing-work-with-the-lightweight-solution-load-feature"></a>Live Unit Testing 如何与轻型解决方案加载功能一起工作？ 

**答：**

如果解决方案中的所有项目尚未进行加载，则 Live Unit Testing 当前无法有效地与轻型解决方案加载功能一起工作。 在这种情况下，可能会获取不正确的覆盖率信息。
 
## <a name="why-does-live-unit-testing-does-not-capture-coverage-from-a-new-process-created-by-a-test"></a>为什么 Live Unit Testing 不会从由测试创建的新进程中捕获覆盖率？
 
**答：**

这是一个已知的问题，我们无法在 Visual Studio 2017 版本中修复。 它应可在 Visual Studio 2017 的后续更新中得到修复。 

## <a name="why-does-nothing-happen-after-i-include-or-exclude-tests-from-the-live-test-set"></a>从 Live Test 集中包含或排除测试后，为什么未执行任何操作？ 

**答：**

这是一个已知问题。 若要解决此问题，需要在包含或排除测试后，对任何文件进行编辑。  

## <a name="live-unit-testing-and-editor-icons"></a>Live Unit Testing 和编辑器图标 

**为什么即使 Live Unit Testing 似乎正基于输出窗口中的消息运行测试，但仍在编辑器中看不到任何图标？** 

**答：**

如果 Live Unit Testing 正在操作的程序集出于任何原因未进行检测，将发生这种情况。 例如，Live Unit Testing 与设置 `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>` 的项目不兼容。 在这种情况下，需要更新生成过程，删除此设置或将其更改为 `true` 以使 Live Unit Testing 工作。  

## <a name="how-do-i-collect-more-detailed-logs-to-file-bug-reports"></a>如何收集更详细的日志到文件 Bug 报告？ 

**答：**

可以执行以下几个操作来收集更详细的日志： 

- 转到“工具”、“选项”、“Live Unit Testing”，将日志记录选项更改为“详细”。 这会使显示在输出窗口中的日志更详细。 

- 将 `LiveUnitTesting_BuildLog` 用户环境变量设置为想要用于捕获 MSBuild 日志的文件名称。 然后就可从该文件中检索 Live Unit Testing 生成中详细的 MSBuild 日志消息。

- 创建一个名为 `VS_UTE_DIAGNOSTICS` 的用户级环境变量并将其设置为 1（或任何值），然后重启 Visual Studio。 现在，应可在 Visual Studio 中的“输出”–“测试”选项卡看到大量日志记录。 
 
## <a name="see-also"></a>另请参阅

[实时单元测试](live-unit-testing.md)
 
