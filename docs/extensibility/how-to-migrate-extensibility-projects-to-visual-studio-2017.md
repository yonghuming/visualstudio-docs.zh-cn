---
title: "如何︰ 将扩展性项目迁移到 Visual Studio 2017 |Microsoft 文档"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
caps.latest.revision: 1
author: gregvanl
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5b6334c38a6c058f274498c06f8e07c934931910
ms.openlocfilehash: efd17a3317302fedcb9bd42aded7a38adee2f75f
ms.lasthandoff: 03/22/2017

---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>如何︰ 迁移到 Visual Studio 2017 扩展性项目

本文档介绍如何将可扩展性项目升级到 Visual Studio 2017。 除了介绍如何更新项目文件，它还描述如何从扩展清单版本 2 (VSIX v2) 升级到新的版本 3 VSIX 清单格式 (VSIX v3)。

## <a name="install-visual-studio-2017-with-required-workloads"></a>安装 Visual Studio 2017 具有所需的工作负荷

请确保您的安装包括以下工作负荷︰

* .NET 桌面开发
* Visual Studio 扩展开发

## <a name="open-vsix-solution-in-visual-studio-2017"></a>在 Visual Studio 2017 中打开 VSIX 解决方案

VSIX 项目中所有需要的主要版本单向升级到 Visual Studio 2017。

将更新项目文件 (例如 *.csproj):

* MinimumVisualStudioVersion-现在将设置为 15.0
* OldToolsVersion (如果以前存在)-现在将设置为 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>更新 Microsoft.VSSDK.BuildTools NuGet 包

>**注意︰**如果您的解决方案不引用 Microsoft.VSSDK.BuildTools NuGet 包，您可以跳过此步骤。

若要生成您的扩展在新的 VSIX v3 （版本 3） 格式，您的解决方案将需要使用新的 VSSDK 构建工具生成。 此功能将安装与 Visual Studio 2017，但您的 VSIX v2 扩展可能会保持到通过 NuGet 较旧版本的引用。 如果是这样，您将需要手动安装更新 Microsoft.VSSDK.BuildTools NuGet 程序包为您的解决方案。

若要更新对 Microsoft.VSSDK.BuildTools 的 NuGet 引用︰

* 右击该解决方案，然后选择**为解决方案管理 NuGet 包...**
* 导航到**更新**选项卡。
* 选择 Microsoft.VSSDK.BuildTools （最新版本）。
* 按**更新**。

![VSSDK 生成工具](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>对 VSIX 扩展清单进行更改

若要确保用户的安装的 Visual Studio 具有运行扩展所需的所有程序集，请指定扩展清单文件中的所有系统必备组件或程序包。 当用户尝试安装该扩展时，VSIXInstaller 将检查以确定是否安装所有必备软件。 如果丢失了一些，则将提示用户以作为扩展安装过程的一部分安装缺少的组件。

>**注意︰**最低限度上，所有扩展应都指定 Visual Studio 核心编辑器组件为系统必备组件。

* 编辑扩展清单文件 （通常称为 source.extension.vsixmanifest）。
* 确保`InstallationTarget`包括 15.0。
* 添加所需的安装系统必备组件 （如在下面的示例所示）。
  * 我们建议您指定仅安装系统必备组件的组件 Id。
  * 请参阅本文档末尾的部分[标识组件 Id 的说明](#finding-component-ids)。

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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>选项︰ 使用设计器对 VSIX 扩展清单进行更改

而不是直接编辑该清单的 XML，可以使用新**先决条件**清单设计器选择必备组件和 XML 的选项卡将为您更新。

>**注意︰**清单设计器只允许您选择当前的 Visual Studio 实例安装的组件 （不工作负荷或包）。 如果您需要添加为工作负荷、 包或当前未安装的组件的必备组件，直接编辑 XML 清单。

* 打开 source.extension.vsixmanifest [设计] 文件。
* 选择**先决条件**选项卡，然后按**新建**按钮。

  ![VSIX 清单设计器](media/vsix-manifest-designer.png)

* **添加新系统必备**将会打开窗口。

  ![添加 vsix 必备组件](media/add-vsix-prerequisite.png)

* 单击下拉列表中为**名称**，然后选择所需的必备组件。
* 如果需要，更新的版本。

  >注意: 版本字段将预先填充了具有范围跨越多达 （但不是包括） 的当前已安装组件的版本的组件的下一个主版本。

  ![添加 roslyn 必备组件](media/add-roslyn-prerequisite.png)

* Press **OK**.

## <a name="if-migrating-from-preview-4-or-preview-5"></a>如果从预览 4 或 5，预览迁移

* 替换`SetupDependencies`与`Prerequisites`和移动元素外的`Installer`元素。 `Prerequisites`现在直接深入了解过长`PackageManifest`元素。
* [可选]删除`GenerateVsixV3`元素。 （这被必需的预览 5 中仅。）`GenerateVsixV3`预览 5 以外的版本中，元素将被忽略。

## <a name="update-debug-settings-for-project"></a>更新项目的调试设置

如果你想要调试您的 Visual Studio 的实验实例中的扩展，请确保项目设置**调试** > **启动操作**具有**启动外部程序︰**值设置为您的 Visual Studio 2017 安装的 devenv.exe 文件。

它可能如下所示︰

```
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe
```

![启动外部程序](media/start-external-program.png)

>**注意︰**调试启动操作通常存储在。 csproj.user 文件。 此文件通常包含在.gitignore 文件，并因此，不正常情况下会保存其他项目时使用文件提交到源代码管理。 在这种情况下，如果已拉入您的解决方案从源代码管理全新很可能此项目将具有为启动操作设置的任何值。 必须使用 Visual Studio 2017 创建的新 VSIX 项目。 csproj.user 文件以指向当前 Visual Studio 安装目录的默认设置创建。 但是如果您要迁移的 VSIX v2 扩展插件，则很可能的。 csproj.user 文件将包含到上一 Visual Studio 版本的安装目录的引用。 设置值的**调试** > **启动操作**将允许正确的 Visual Studio 实验实例，以启动 when you try to 调试您的扩展。

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>检查扩展构建正确 （如 VSIX v3)

* 生成 VSIX 项目。
* 将解压缩生成的 VSIX。
  * 通过默认情况下，在 bin/Debug 的 VSIX 文件生活或 bin/Release 作为 [YourCustomExtension].vsix。
  * 重命名为.zip，轻松地查看的内容的.vsix。
* 检查存在三个文件︰
  * extension.vsixmanifest
  * manifest.json
  * catalog.json

## <a name="check-when-all-required-prerequisites-are-installed"></a>检查安装了所有所需的必备组件

VSIX 将会成功安装在计算机并且所需的所有系统必备组件安装的测试。

>**注意︰**在安装之前的任何扩展名，请关闭 Visual Studio 的所有实例。

尝试安装该扩展︰

* 在 Visual Studio 2017

![在 Visual Studio 2017 VSIX 安装程序](media/vsixinstaller-vs-2017.png)

* Visual Studio 的早期版本的可选︰ 检查。
  * 证明向后兼容性。
  * 应该适用于 Visual Studio 2012、 Visual Studio 2013、 Visual Studio 2015。
* 可选︰ 检查 VSIX 安装程序版本检查器提供了一种版本。
  * 包括 Visual Studio 的早期版本 （如果已安装）。
  * 包括 Visual Studio 2017。

如果最近打开 Visual Studio，您可能会看到如下对话框︰

![正在运行的进程的 vs](media/vs-running-processes.png)

等待进程关闭，或者手动结束任务。 按照所列的名称，或使用在括号中列出的 PID，您可以找到这些进程。

>**注意︰**这些进程将不会自动关闭 Visual Studio 的实例正在运行时。 请确保已关闭的情况下在计算机 – 包括来自其他用户，使用 Visual Studio 的所有实例，然后继续重试。

## <a name="check-when-missing-the-required-prerequisites"></a>缺少所需的必备组件时检查

* 尝试安装该扩展的计算机上使用 Visual Studio 2017 不包含系统必备组件 （上述） 中定义的所有组件。
* 检查安装标识缺少的组件/s 和列表作为 VSIXInstaller 中的必备组件。
* 注意︰ 提升都会要求提供如果需要使用该扩展安装任何系统必备组件。

![vsixinstaller 缺少的先决条件](media/vsixinstaller-missing-prerequisite.png)

## <a name="deciding-on-components"></a>确定组件

当查找您的依赖关系，您会发现一个依赖关系可映射到多个组件。 若要确定哪些依赖项，您应指定为您的系统必备组件，建议您选择一个组件，它具有类似于您的扩展功能，同时考虑您的用户和哪种类型的组件将很可能已安装或安装不会介意。 我们还建议您的扩展的附加功能和所需的先决条件，满足将允许您扩展运行的最小方式进行处于激活状态，如果某些组件未检测到的构建。

若要进一步提供指导，我们已确定几个常见的扩展类型和其建议的系统必备组件︰

扩展类型 | 显示名称 |    Id
--- | --- | ---
编辑器 | Visual Studio 核心编辑器    | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# 和 Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | 管理桌面工作负荷核心 | Microsoft.VisualStudio.Component.ManagedDesktop.Core
调试器 | 在实时调试器 | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="finding-component-ids"></a>查找组件 Id

Visual Studio 产品按排序的组件列表中位于[Visual Studio 2017 工作负荷和组件 Id](https://aka.ms/vs2017componentIDs)。 为您必备 Id 在清单中使用这些组件 Id。

如果您不确定哪个组件包含特定的二进制文件，下载[-> 二进制映射电子表格组件](https://aka.ms/vs2017componentid-binaries)。

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017 ComponentBinaryMapping.xlsx

在 Excel 工作表中有四列︰**组件名称**， **ComponentId**，**版本**，和**二进制 / 文件名**。  可以使用筛选器来搜索和查找特定的组件和二进制文件。

对于所有引用，首先确定哪些是核心编辑器 (Microsoft.VisualStudio.Component.CoreEditor) 组件中。  最低保护措施，我们需要指定为所有扩展的必备组件的核心编辑器组件。 也会保留核心编辑器中所没有的引用，将添加中的筛选器**二进制文件 / 文件名称**部分以查找具有的任何子集这些引用的组件。

示例：

* 如果调试器扩展，并且知道您的项目具有 VSDebugEng.dll 和 VSDebug.dll 的参考，请单击中的筛选器按钮**二进制文件 / 文件名称**标头。  搜索"VSDebugEng.dll"并选择确定。  下一步中的筛选器按钮上单击**二进制文件 / 文件名称**再次标头并搜索"VSDebug.dll"。  选中"添加当前所选内容来筛选"的复选框，然后选择确定。  现在请浏览**组件名称**若要查找的组件的大多数与您的扩展类型相关。 在此示例中，您将选择实时调试，并将其添加到您 vsixmanifest。
* 如果您知道您的项目处理调试器元素，您可以搜索在"调试器"筛选器在搜索框中以查看哪些组件包含其名称中的调试器。

