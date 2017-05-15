---
title: "Visual Studio Build Tools 2017 工作负载和组件 ID | Microsoft Docs"
description: "使用 Visual Studio 工作负载和组件 ID 来构建基于 Windows 的经典应用程序"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 05/10/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.prod: visual-studio-dev15
ms.service: 
ms.technology:
- vs-ide-install
ms.assetid: b99298df-0280-47fc-af73-44cd7a8ac553
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
ms.sourcegitcommit: 054126ddbdc9f0144983a1ef21fa43875699cbee
ms.openlocfilehash: 1147438d12d754233f6205de4a5d37920cb5b66a
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---

# <a name="visual-studio-build-tools-2017-component-directory"></a>Visual Studio 生成工具 2017 组件目录

本页中的表中列出了可用于通过命令行安装 Visual Studio 的 ID。 请注意，我们将在发布 Visual Studio 更新时添加其他组件。

另请注意以下有关本页的注意事项：

* 每个工作负载均有其自己的部分，后跟工作负载 ID 和适用于工作负载的组件表格。
* 默认情况下，安装工作负载时将安装**必需**组件。 如果愿意，还可以安装**推荐**和**可选**组件。
* 我们还添加了一个部分，此部分列出了不属于任何工作负载的其他组件。

有关如何使用这些 ID 的详细信息，请参阅[使用命令行参数安装 Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) 页。 另外，有关其他产品的工作负载和组件 ID 的列表，请参阅 [Visual Studio 2017 工作负载和组件 ID](workload-and-component-ids.md) 页。

## <a name="msbuild-tools"></a>MSBuild 工具

**ID：**Microsoft.VisualStudio.Workload.MSBuildTools

**说明：**提供构建基于 MSBuild 的应用程序所需的工具。

### <a name="components-included-by-this-workload"></a>此工作负载所包含的组件

组件 ID | 名称 | 版本 | 依赖项类型
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | 必需
Microsoft.VisualStudio.Component.CoreBuildTools | Visual Studio 生成工具核心 | 15.0.26228.0 | 必需
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 和 Visual Basic Roslyn 编译器 | 15.0.26208.0 | 必需


## <a name="visual-c-build-tools"></a>Visual C++ 生成工具

**ID：**Microsoft.VisualStudio.Workload.VCTools

**说明：**使用功能强大的 Visual C++ 工具集、ATL 以及 MFC 和 C++/CLI 等可选功能生成基于 Windows 的经典应用程序。

### <a name="components-included-by-this-workload"></a>此工作负载所包含的组件

组件 ID | 名称 | 版本 | 依赖项类型
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Visual C++ 生成工具的核心功能 | 15.0.26208.0 | 必需
Microsoft.VisualStudio.Component.Windows10SDK | Windows 通用 C 运行时 | 15.0.26208.0 | 必需
Microsoft.VisualStudio.Component.VC.CMake.Project | 适用于 CMake 的 Visual C++ 工具 | 15.0.26208.0 | 建议
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | 适用于桌面 C++ x86 和 x64 的 Windows 10 SDK (10.0.15063.0) | 15.0.26403.0 | 建议
Microsoft.Component.VC.Runtime.UCRTSDK | Windows 通用 CRT SDK | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目标包 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 静态分析工具 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL 支持 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC 和 ATL 支持（x86 和 x64） | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2（实验） | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | C++/CLI 支持 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ 核心功能 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | 标准库模块 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141 工具集（x86、x64） | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK 和 UCRT SDK | 15.0.26208.0 | Optional


## <a name="web-development-build-tools"></a>Web 开发生成工具

**ID：**Microsoft.VisualStudio.Workload.WebBuildTools

**说明：**用于构建 Web 应用程序的 MSBuild 任务和目标。

### <a name="components-included-by-this-workload"></a>此工作负载所包含的组件

组件 ID | 名称 | 版本 | 依赖项类型
--- | --- | --- | ---
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Web 开发生成工具 | 15.0.26323.1 | 必需
## <a name="unaffiliated-components"></a>独立组件

这些组件不随附于任何工作负载，但可选择作为单个组件。

组件 ID | 名称 | 版本
--- | --- | ---
无 | 不可用 | 无


## <a name="see-also"></a>另请参阅

* [Visual Studio 工作负荷和组件 ID](workload-and-component-ids.md)
* [Visual Studio 管理员指南](visual-studio-administrator-guide.md)
* [使用命令行参数安装 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [命令行参数示例](command-line-parameter-examples.md)
* [创建 Visual Studio 的脱机安装](create-an-offline-installation-of-visual-studio.md)

