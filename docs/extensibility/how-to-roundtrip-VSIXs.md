---
title: "如何： Visual Studio 的往返扩展 |Microsoft 文档"
ms.custom: 
ms.date: 06/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
caps.latest.revision: "1"
author: willbrown
ms.author: willbrown
manager: justinclareburt
ms.openlocfilehash: 99bdd5a0f31b9cbccd84a7c05f6d3cdcc0c267f6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-2017-and-visual-studio-2015"></a>如何： 使扩展与 Visual Studio 2017 和 Visual Studio 2015 兼容

本文档说明如何使扩展性项目 Visual Studio 2015 和 Visual Studio 2017 之间往返。 完成此升级之后，将能够打开、 生成、 安装和运行 Visual Studio 2015 和 Visual Studio 2017 中一个项目。  可以 Visual Studio 2015 和 Visual Studio 2017 之间的往返某些扩展插件可以找到作为参考，[此处](https://github.com/Microsoft/VSSDK-Extensibility-Samples)在 Microsoft 的扩展性示例。

如果你只想要生成在 Visual Studio 2017 年，但希望输出 VSIX 若要运行 Visual Studio 2015 和 Visual Studio 2017 年 1，则引用[扩展迁移文档](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)。

>**注意：**由于在 Visual Studio 版本之间的更改，在一个版本中工作的事件将不适用另一个。 确保在这两个版本中，提供了你尝试访问的功能，或者该扩展将具有意外的结果。

下面是将完成保存/还原 VSIX 本文档中的步骤概述：

1. 导入正确的 NuGet 包。
2. 更新扩展清单：
    * 安装目标
    * 先决条件
3. 更新 CSProj:
    * 更新`<MinimumVisualStudioVersion>`。
    * 添加`<VsixType>`属性。
    * 添加调试属性`($DevEnvDir)`3 次。
    * 添加用于导入生成工具和目标的条件。

4. 生成和测试

## <a name="environment-setup"></a>环境设置

本文档假定你具有您的计算机上安装以下产品：

* 使用 VS SDK 安装的 visual Studio 2015
* 与安装扩展性工作负荷的 visual Studio 2017

## <a name="recommended-approach"></a>建议的方法

强烈建议使用 Visual Studio 2015 中，而不是 Visual Studio 2017 启动此升级。 在 Visual Studio 2015 中开发的主要优势是确保不引用在 Visual Studio 2015 中不可用的程序集。 如果确实有 Visual Studio 自 2017 年中的开发，则可能会引入依赖于只在 Visual Studio 2017 中存在的程序集的风险。

## <a name="ensure-there-is-no-reference-to-projectjson"></a>确保未对 project.json 引用

更高版本在本文档中，我们将插入到 *.csproj 文件中的条件的导入语句。  这不起作用，如果你 NuGet 引用存储在 project.json。 在这种情况下，建议将移到 packages.config 文件的所有 NuGet 引用。
如果你的项目包含 project.json 文件：

* 记下在 project.json 中的引用。
* 从解决方案资源管理器，删除项目中的 project.json 文件。
    * 这将删除 project.json 文件，并从项目中删除它。
* 添加 NuGet 引用回项目。
    * 右键单击解决方案并选择**管理解决方案的 NuGet 包...**
    * Visual Studio 自动为你创建 packages.config 文件

>**注意：**如果你的项目包含 EnvDTE 包，它们可能需要通过右键单击要添加**引用**选择**添加引用**并添加了相应的引用。  使用 NuGet 包可能在尝试生成项目时创建错误。

## <a name="adding-appropriate-build-tools"></a>添加相应的生成工具

我们以确保需要添加将使我们能够生成和调试适当的生成工具。 Microsoft 创建了此调用 Microsoft.VisualStudio.Sdk.BuildTasks 程序集。

若要生成并部署在 Visual Studio 2015 和 2017 VSIXv3，你将需要以下 NuGet 包：

版本 | 生成的工具
--- | ---
Visual Studio 2015 | Microsoft.VisualStudio.Sdk.BuildTasks.14.0
Visual Studio 2017 | Microsoft.VSSDK.BuildTool

若要这样做：

* 将 NuGet 包 Microsoft.VisualStudio.Sdk.BuildTasks.14.0 添加到你的项目。
* 如果你的项目不包含 Microsoft.VSSDK.BuildTools，请将其添加。
* 请确保 Microsoft.VSSDK.BuildTools 版本为 15.x 或更高版本。

## <a name="update-extension-manifest"></a>更新扩展清单

### <a name="1-installation-targets"></a>1.安装目标

我们需要告诉以用于构建 VSIX 面向哪些版本的 Visual Studio。  通常，这些引用是到版本 14.0 (Visual Studio 2015) 或版本 15.0 (Visual Studio 2017)。  在本例中，我们想要生成将安装的扩展对于两者来说，因此我们需要将这两个版本的 VSIX。  如果你想要生成并早于 14.0 版本上安装你 VSIX，这可以通过设置的更早版本的版本号;但是，不再支持版本 10.0 和更早版本。

* 在 Visual Studio 中打开 source.extension.vsixmanifest 文件。
* 打开**安装目标**选项卡。
* 更改**版本范围**到 [14.0，16.0）。  [告知 Visual Studio 包括过去它 14.0 和所有版本。  ) 告知 Visual Studio 包括 15.0 到，但不是包括版本 16.0 的所有版本。
* 保存所有更改并关闭 Visual Studio 的所有实例。

![安装目标图像](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2.添加 extension.vsixmanifest 文件的先决条件

系统必备组件是使用 Visual Studio 2017 的新功能。  在这种情况下，我们需要 Visual Studio 核心编辑器作为必备组件。 由于 Visual Studio 2015 VSIX 设计器不处理新`Prerequisites`部分中，你将需要编辑在 XML 代码中手动此部件。  或者，你可以打开 Visual Studio 2017 和更新清单设计器用于插入系统必备组件。

若要手动此操作：

* 导航到文件资源管理器中的项目目录。
* 打开`extension.vsixmanifest`使用文本编辑器的文件。
* 添加以下标记：

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* 保存并关闭文件。

>**注意：**如果你选择实现此目的在 Visual Studio 2017 的 VSIX 设计，你将需要手动编辑必备组件的版本，以确保它是与所有版本的 Visual Studio 2017 兼容。  这是因为设计器将插入的最低版本为当前版本的 Visual Studio (例如，15.0.26208.0)。  但是，由于其他用户可能具有较早版本，你将希望手动编辑此到 15.0。

此时，你的清单文件应如下所示：

![前提条件示例](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>修改项目文件 (myproject.csproj)

强烈建议以修改.csproj 打开时执行此步骤的引用。  你可以找到的几个示例[此处](https://github.com/Microsoft/VSSDK-Extensibility-Samples)。  选择任何扩展性示例，查找引用将.csproj 文件，然后执行以下步骤：

* 导航到文件资源管理器中的项目目录。
* 使用文本编辑器打开 myproject.csproj 文件。

### <a name="1-update-the-minimumvisualstudioversion"></a>1.更新 MinimumVisualStudioVersion

* 将最小的 visual studio 版本设置为`$(VisualStudioVersion)`和为其添加条件语句。  如果不存在，请添加这些标记。  确保标记设置如下所示：

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2.添加 VsixType 属性

* 添加以下标记`<VsixType>v3</VsixType>`到属性组。

>**注意：**建议地将其添加下面`<OutputType></OutputType>`标记。

### <a name="3-add-the-debugging-properties"></a>3.添加的调试属性

* 添加以下属性组：

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartPrograms>$(DevEnvDir)devenv.exe</StartPrograms>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* 从将.csproj 文件和任何删除以下的所有实例。 csproj.user 文件：

```xml
<StartAction>Program</StartAction>
<StartPrograms>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartPrograms>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4.将条件添加到生成工具导入

* 添加到的其他条件语句`<import>`Microsoft.VSSDK.BuildTools 引用的标记。  执行此操作的方法是插入`'$(VisualStudioVersion)' != '14.0' And`在条件语句的前面。  这些语句将出现在页眉和页脚 csproj 文件。

例如: 

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201… Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…/>
```

* 添加到的其他条件语句`<import>`具有 Microsoft.VisualStudio.Sdk.BuildTasks.14.0 的标记。  执行此操作的方法是插入`'$(VisualStudioVersion)' == '14.0' And`在条件语句的前面。 这些语句将出现在页眉和页脚 csproj 文件。

例如: 

```xml
<Import Project="packages\ Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0… Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…/>
```

* 添加到的其他条件语句`<Error>`Microsoft.VSSDK.BuildTools 引用的标记。  执行此操作的方法是插入`'$(VisualStudioVersion)' != '14.0' And`在条件语句的前面。 这些语句将出现在 csproj 文件尾。

例如: 

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…/>
```

* 添加到的其他条件语句`<Error>`具有 Microsoft.VisualStudio.Sdk.BuildTasks.14.0 的标记。  执行此操作的方法是插入`'$(VisualStudioVersion)' == '14.0' And`在条件语句的前面。 这些语句将出现在 csproj 文件尾。

例如: 

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\ Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…/>
```

* 保存 csproj 文件并将其关闭。

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2017"></a>在 Visual Studio 2015 和 Visual Studio 2017 中测试扩展安装

此时，你的项目应该已准备好生成可以安装于 Visual Studio 2015 和 Visual Studio 2017 VSIXv3。

* 在 Visual Studio 2015 中打开你的项目
* 生成你的项目，并确认 VSIX 正确生成的输出
* 导航到你的项目目录
* 打开 bin-> 调试文件夹
* 双击该 VSIX 文件，在 Visual Studio 2015 和 Visual Studio 2017 上安装你的扩展
* 确保你可以看到-> 扩展和更新"已安装"部分中的工具中的扩展。
* 尝试运行/使用要检查其正常运行的扩展

![查找 VSIX](media/finding-a-VSIX-example.png)

>**注意：**如果你的项目挂起消息"打开文件"强制关闭 Visual Studio 中，导航到你的项目目录、 显示隐藏的文件夹，并删除.vs 文件夹。
