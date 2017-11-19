---
title: "如何： 将扩展性项目迁移到 Visual Studio 2017 |Microsoft 文档"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 89591535b232317abf395c237fdc267c847ca699
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>如何： 将扩展性项目迁移到 Visual Studio 2017

本文档说明如何将扩展性项目升级到 Visual Studio 2017。 除了介绍如何更新项目文件，它还描述如何从扩展清单版本 2 (VSIX v2) 升级到新的版本 3 VSIX 清单格式 (VSIX v3)。

## <a name="install-visual-studio-2017-with-required-workloads"></a>安装 Visual Studio 2017 具有所需的工作负荷

请确保你安装包括以下工作负荷：

* .NET 桌面开发
* Visual Studio 扩展开发

## <a name="open-vsix-solution-in-visual-studio-2017"></a>在 Visual Studio 2017 中打开 VSIX 解决方案

所有 VSIX 项目将都需要将主要版本单向升级至 Visual Studio 2017。

将更新项目文件 (例如 *.csproj):

* MinimumVisualStudioVersion-现在设置为 15.0
* OldToolsVersion (如果以前存在)-现在设置为 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>更新 Microsoft.VSSDK.BuildTools NuGet 包

>**注意：**如果你的解决方案不引用 Microsoft.VSSDK.BuildTools NuGet 包，则可以跳过此步骤。

若要生成你的扩展中新的 VSIX v3 （版本 3） 格式，你的解决方案将需要使用新的 VSSDK 生成工具生成。 此功能将安装与 Visual Studio 2017 年，但你的 VSIX v2 扩展可能保持通过 NuGet 较旧版本的引用。 如果是这样，你将需要手动安装你的解决方案的 Microsoft.VSSDK.BuildTools NuGet 包的更新。

更新对 Microsoft.VSSDK.BuildTools 的 NuGet 引用：

* 右键单击解决方案并选择**管理解决方案的 NuGet 包...**
* 导航到**更新**选项卡。
* 选择 Microsoft.VSSDK.BuildTools （最新版本）。
* 按**更新**。

![VSSDK 生成工具](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>对 VSIX 扩展清单进行更改

若要确保用户的安装的 Visual Studio 具有运行扩展所需的所有程序集，指定扩展清单文件中的所有系统必备组件或包。 当用户尝试安装该扩展时，VSIXInstaller 将检查是否安装了所有系统必备组件。 如果丢失了一些，则将提示用户以扩展安装过程的一部分安装缺少的组件。

>**注意：**在最低限度上，所有扩展应都指定 Visual Studio 核心编辑器组件作为系统必备组件。

* 编辑扩展清单文件 （通常称为 source.extension.vsixmanifest）。
* 确保`InstallationTarget`包括 15.0。
* 添加所需的安装系统必备组件 （如下面的示例中所示）。
  * 我们建议指定仅组件的安装必备组件的 Id。
  * 请参阅本文档的结尾部分[标识组件 Id 的说明](#finding-component-ids)。

示例:

```xml
<PackageManifest>
 ...
    <Prerequisites>
        <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Component.DiagnosticTools" Version="[15.0.25814.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Shell.12.0" Version="[12.0]" />
    </Prerequisites>
 ...
</PackageManifest>
```

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>选项： 使用设计器对 VSIX 扩展清单进行更改

而不是直接编辑的清单 XML，可以使用新**先决条件**将为你更新清单设计器选择必备组件和 XML 的选项卡。

>**注意：**清单设计器将只允许你选择当前的 Visual Studio 实例安装的组件 （不工作负荷或包）。 如果你需要添加对工作负荷、 包或当前未安装的组件的先决条件，请直接编辑 XML 清单。

* 打开 source.extension.vsixmanifest [设计] 文件。
* 选择**先决条件**选项卡并按**新建**按钮。

  ![VSIX 清单设计器](media/vsix-manifest-designer.png)

* **添加新先决条件**窗口将打开。

  ![添加 vsix 必备组件](media/add-vsix-prerequisite.png)

* 上的下拉列表中单击**名称**和选择所需的必备组件。
* 如果需要，更新的版本。

  >注意： 版本字段将预先填充了具有最多跨越范围 （但不是包括） 的当前安装组件的版本组件的下一个主要版本。

  ![添加 roslyn 必备组件](media/add-roslyn-prerequisite.png)

* Press **OK**.

## <a name="if-migrating-from-preview-4-or-preview-5"></a>如果从 Preview 4 或 Preview 5 中迁移

* 替换`SetupDependencies`与`Prerequisites`和移动外的元素`Installer`元素。 `Prerequisites`现在直接在位于`PackageManifest`元素。
* [可选]删除`GenerateVsixV3`元素。 （需要此项 Preview 5 中仅。）`GenerateVsixV3`元素将在 Preview 5 之外的版本中被忽略。

## <a name="update-debug-settings-for-project"></a>更新项目的调试的设置

如果你想要调试你的 Visual Studio 的实验实例中的扩展，请确保项目设置**调试** > **启动操作**具有**启动外部程序：**值设置为你的 Visual Studio 2017 安装的 devenv.exe 文件。

它可能如下所示：

```
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe
```

![启动外部程序](media/start-external-program.png)

>**注意：**调试启动操作通常存储在。 csproj.user 文件。 此文件通常包含在.gitignore 文件，并因此，通常不会保存与其他项目文件时提交到源代码管理。 在这种情况下，仅当你具有请求你的解决方案从源代码管理全新很可能此项目将具有为启动操作设置任何值。 使用 Visual Studio 2017 创建的新 VSIX 项目将具有。 csproj.user 文件以指向当前的 Visual Studio 安装目录的默认设置创建。 但是如果你要迁移的 VSIX v2 扩展，则很可能的。 csproj.user 文件将包含以前的 Visual Studio 版本的安装目录的引用。 值设置**调试** > **启动操作**将允许正确的 Visual Studio 实验实例，以在你尝试调试你的扩展时启动。

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>检查扩展生成正确 （作为 VSIX v3)

* 生成 VSIX 项目。
* 解压缩生成的 VSIX。
  * 通过默认情况下，在 bin/Debug 的 VSIX 文件生活或 bin/发布作为 [YourCustomExtension].vsix。
  * 将.vsix 重命名为.zip 轻松查看的内容。
* 检查存在的三个文件：
  * extension.vsixmanifest
  * manifest.json
  * catalog.json

## <a name="check-when-all-required-prerequisites-are-installed"></a>时安装所有必需的先决条件检查

VSIX 成功安装在计算机并且所有所需的系统必备组件安装的测试。

>**注意：**然后再安装任何扩展，请关闭 Visual Studio 的所有实例。

尝试安装该扩展：

* 在 Visual Studio 2017

![在 Visual Studio 2017 VSIX 安装程序](media/vsixinstaller-vs-2017.png)

* 可选： 检查以前版本的 Visual Studio。
  * 证明向后兼容性。
  * 也适用于 Visual Studio 2012、 Visual Studio 2013、 Visual Studio 2015。
* 可选： 检查 VSIX 安装程序版本检查器提供了一种版本。
  * 包括以前版本的 Visual Studio （如果已安装）。
  * 包括 Visual Studio 2017。

如果最近打开 Visual Studio，你可能会看到如下对话框：

![vs 正在运行的进程](media/vs-running-processes.png)

等待进程后，才可关闭，或手动结束任务。 你可以发现进程，按列出的名称，或使用括号中列出的 PID。

>**注意：**这些进程将不会自动关闭时 Visual Studio 的实例正在运行。 请确保已关闭上机-包括来自其他用户的 Visual Studio 的所有实例，然后继续重试。

## <a name="check-when-missing-the-required-prerequisites"></a>时缺少所需的先决条件检查

* 尝试安装扩展的计算机上使用 Visual Studio 2017 该并不包含系统必备组件 （上述） 中定义的所有组件。
* 检查安装标识缺失的组件/s 和列为 VSIXInstaller 中的必备组件。
* 注意： 提升将如果需要任何系统必备组件需要安装了扩展。

![vsixinstaller 缺少的必备项](media/vsixinstaller-missing-prerequisite.png)

## <a name="deciding-on-components"></a>确定组件

当查找依赖项，您会发现一个依赖关系无法将映射到多个组件。 若要确定哪些依赖关系，你应指定为你系统必备组件，我们建议你选择具有类似于你的扩展的功能的组件和同时考虑你的用户和哪种类型的组件将它们很可能已安装或是不会介意安装。 我们还建议你在所需的先决条件满足将允许你扩展运行的最小的其中一种方法并对其他功能的扩展将它们处于激活状态，如果某些组件未检测到的构建。

若要提供更多指南，我们已识别几个常见的扩展类型和其建议的系统必备组件：

扩展类型 | 显示名称 | Id
--- | --- | ---
编辑器 | Visual Studio 核心编辑器  | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# 和 Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | 托管桌面工作负载核心 | Microsoft.VisualStudio.Component.ManagedDesktop.Core
调试器 | 实时调试器 | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="finding-component-ids"></a>查找组件 Id

Visual Studio 产品按排序的组件的列表位于[Visual Studio 2017 工作负荷和组件 Id](https://aka.ms/vs2017componentIDs)。 为你的系统必备 Id 在清单中使用这些组件 Id。

如果您不确定哪个组件包含特定的二进制文件，下载[组件-> 二进制映射电子表格](https://aka.ms/vs2017componentid-binaries)。

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017 ComponentBinaryMapping.xlsx

Excel 工作表中有四列：**组件名称**， **ComponentId**，**版本**，和**二进制 / 文件名称**。  可以使用筛选器来搜索和查找特定组件和二进制文件。

对于所有引用，首先确定哪些是核心编辑器 (Microsoft.VisualStudio.Component.CoreEditor) 组件中。  最小，我们需要指定为所有扩展的必备组件的核心编辑器组件。 将保留不在核心编辑器中的引用，添加中的筛选器**二进制文件 / 文件名称**部分以查找具有以下任一这些引用的子集的组件。

示例：

* 如果你具有调试器扩展名，并且知道你的项目具有对 VSDebugEng.dll 和 VSDebug.dll 的引用，请单击中的筛选器按钮上**二进制文件 / 文件名称**标头。  搜索"VSDebugEng.dll"，然后选择确定。  下一步中的筛选器按钮单击**二进制文件 / 文件名称**标头再次然后搜索"VSDebug.dll"。  选择"添加当前所选内容来筛选"的复选框，然后选择确定。  现在浏览**组件名称**查找是大多数组件与您的扩展类型相关。 在此示例中，你将选择实时调试器并将其添加到你 vsixmanifest。
* 如果你知道你的项目处理调试器元素，你可以搜索"调试器"筛选器搜索框中以查看哪些组件包含在其名称中的调试器。
