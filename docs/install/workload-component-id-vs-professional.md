---
title:
- "Visual Studio Professional 2017 工作负载和组件 ID | Microsoft Docs"
description: "使用工作负载和组件 ID 通过命令行安装 Visual Studio 或指定为 VSIX 清单中的依赖项"
keywords: 
author:
- TerryGLee
ms.author:
- tglee
manager:
- ghogen
ms.date: 03/07/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.prod: visual-studio-dev15
ms.service: 
ms.technology:
- vs-ide-install
- vs-ide-sdk
ms.assetid: 5719032b-2c2e-416e-a281-a4573ec74e38
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
translationtype: Human Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 1f2da4c8c70c36b3a521ac094c0bf9658897a9c0
ms.lasthandoff: 03/07/2017

---

# <a name="visual-studio-professional-2017-component-directory"></a>Visual Studio Professional 2017 组件目录

本页的表中列出了可用于通过使用命令行安装 Visual Studio 或可指定为 VSIX 清单中的依赖项的 ID。 请注意，我们将在发布 Visual Studio 更新时添加其他组件。

另请注意以下有关本页的注意事项：

* 每个工作负载均有其自己的部分，后跟工作负载 ID 和适用于工作负载的组件表格。
* 默认情况下，安装工作负载时将安装**必需**组件。 如果愿意，还可以安装**推荐**和**可选**组件。
* 我们还添加了一个部分，此部分列出了不属于任何工作负载的其他组件。

在 VSIX 清单中设置依赖项时，必须仅指定组件 ID。 使用本页中的表格来确定最小组件依赖项。 在某些情况下，这可能意味着仅从工作负载指定一个组件。 在其他情况下，这可能意味着你从单个工作负载指定多个组件或从多个工作负载指定多个组件。 有关详细信息，请参阅[如何：将扩展性项目迁移到 Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) 页。

有关如何使用这些 ID 的详细信息，请参阅[使用命令行参数安装 Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) 页。 另外，有关其他产品的工作负载和组件 ID 的列表，请参阅 [Visual Studio 2017 工作负载和组件 ID](workload-and-component-ids.md) 页。

## <a name="visual-studio-core-editor-included-with-visual-studio-professional-2017"></a>Visual Studio 核心编辑器（Visual Studio Professional 2017 随附）

**ID：**Microsoft.VisualStudio.Workload.CoreEditor

**说明：**Visual Studio 核心 shell 体验，包括语法感知代码编辑、源代码管理和工作项管理。

### <a name="components-included-by-this-workload"></a>此工作负载所包含的组件

组件 ID | 名称 | 依赖项类型
--- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio 核心编辑器 | 必需


## <a name="azure-development"></a>Azure 开发

**ID：**Microsoft.VisualStudio.Workload.Azure

**说明：**用于开发云应用和创建资源的 Azure SDK、工具和项目。

### <a name="components-included-by-this-workload"></a>此工作负载所包含的组件

组件 ID | 名称 | 依赖项类型
--- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 必需
Microsoft.Component.NetFX.Core.Runtime | .NET Core 运行时 | 必需
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 必需
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目标包 | 必需
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET framework 4.6.1 开发工具 | 必需
Microsoft.Net.Core.Component.SDK | .NET Core 1.0.1 开发工具 | 必需
Microsoft.NetCore.ComponentGroup.Web | .NET Core 1.0 - 1.1 开发工具 | 必需
Microsoft.VisualStudio.Component.Azure.ClientLibs | .NET 的 Azure 库 | 必需
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 必需
Microsoft.VisualStudio.Component.Common.Azure.Tools | 连接和发布工具 | 必需
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 必需
Microsoft.VisualStudio.Component.NuGet | NuGet 程序包管理器 | 必需
Microsoft.VisualStudio.Component.PortableLibrary | .NET 可移植库目标包 | 必需
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 和 Visual Basic Roslyn 编译器 | 必需
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Azure 开发必备组件 | 必需
Component.WebSocket | WebSocket4Net | 建议
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake 工具 | 建议
Microsoft.Component.ClickOnce | ClickOnce 发布 | 建议
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 目标包 | 建议
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目标包 | 建议
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目标包 | 建议
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目标包 | 建议
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目标包 | 建议
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 开发工具 | 建议
Microsoft.VisualStudio.Component.AppInsights.Tools | 开发人员分析工具 | 建议
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure 创作工具 | 建议
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure 计算仿真程序 | 建议
Microsoft.VisualStudio.Component.Azure.MobileAppsSdk | Azure 移动应用 SDK | 建议
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Azure Resource Manager 核心工具 | 建议
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Service Fabric 工具 | 建议
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure 存储仿真程序 | 建议
Microsoft.VisualStudio.Component.Azure.Waverton | Azure 云服务核心工具 | 建议
Microsoft.VisualStudio.Component.DiagnosticTools | 分析工具 | 建议
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 建议
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 诊断 | 建议
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 和 TypeScript 语言支持 | 建议
Microsoft.VisualStudio.Component.ManagedDesktop.Core | 托管桌面工作负载核心 | 建议
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 建议
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 运行时 | 建议
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 数据类型 | 建议
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server 命令行实用工具 | 建议
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 支持的数据源 | 建议
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 建议
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 建议
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 建议
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 静态分析工具 | 建议
Microsoft.VisualStudio.Component.TextTemplating | 文本模板转换 | 建议
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 建议
Microsoft.VisualStudio.Component.VisualStudioData | 数据源和服务引用 | 建议
Microsoft.VisualStudio.Component.Web | ASP.NET 和 Web 开发工具 | 建议
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 建议
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Azure 云服务工具 | 建议
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Azure Resource Manager 工具 | 建议
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 目标包 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 开发工具 | Optional
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Azure 存储 AzCopy | Optional
Microsoft.VisualStudio.Component.PowerShell.Tools | PowerShell 工具 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | Optional


## <a name="data-storage-and-processing"></a>数据存储和处理

**ID：**Microsoft.VisualStudio.Workload.Data

**说明：**使用 SQL Server、Azure Data Lake、Hadoop 或 Azure ML 连接、开发和测试数据解决方案。

### <a name="components-included-by-this-workload"></a>此工作负载所包含的组件

组件 ID | 名称 | 依赖项类型
--- | --- | ---
Component.Redgate.ReadyRoll | Redgate ReadyRoll | 建议
Component.Redgate.SQLPrompt.VsPackage | Redgate SQL Prompt | 建议
Component.Redgate.SQLSearch.VSExtension | Redgate SQL Search | 建议
Component.WebSocket | WebSocket4Net | 建议
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake 工具 | 建议
Microsoft.Component.ClickOnce | ClickOnce 发布 | 建议
Microsoft.Component.MSBuild | MSBuild | 建议
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 目标包 | 建议
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目标包 | 建议
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目标包 | 建议
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 建议
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目标包 | 建议
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目标包 | 建议
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目标包 | 建议
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET framework 4.6.1 开发工具 | 建议
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 开发工具 | 建议
Microsoft.VisualStudio.Component.AppInsights.Tools | 开发人员分析工具 | 建议
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure 创作工具 | 建议
Microsoft.VisualStudio.Component.Azure.ClientLibs | .NET 的 Azure 库 | 建议
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure 计算仿真程序 | 建议
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure 存储仿真程序 | 建议
Microsoft.VisualStudio.Component.Azure.Waverton | Azure 云服务核心工具 | 建议
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 建议
Microsoft.VisualStudio.Component.Common.Azure.Tools | 连接和发布工具 | 建议
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 建议
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 诊断 | 建议
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 和 TypeScript 语言支持 | 建议
Microsoft.VisualStudio.Component.ManagedDesktop.Core | 托管桌面工作负载核心 | 建议
Microsoft.VisualStudio.Component.NuGet | NuGet 程序包管理器 | 建议
Microsoft.VisualStudio.Component.PortableLibrary | .NET 可移植库目标包 | 建议
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 和 Visual Basic Roslyn 编译器 | 建议
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 建议
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 运行时 | 建议
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 数据类型 | 建议
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server 命令行实用工具 | 建议
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 支持的数据源 | 建议
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 建议
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 建议
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 建议
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 静态分析工具 | 建议
Microsoft.VisualStudio.Component.TextTemplating | 文本模板转换 | 建议
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 建议
Microsoft.VisualStudio.Component.VisualStudioData | 数据源和服务引用 | 建议
Microsoft.VisualStudio.Component.Web | ASP.NET 和 Web 开发工具 | 建议
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 建议
Microsoft.VisualStudio.Component.FSharp | F# 语言支持 | Optional


## <a name="net-desktop-development"></a>.NET 桌面开发

**ID：**Microsoft.VisualStudio.Workload.ManagedDesktop

**说明：**使用 .NET Framework 生成 WPF、Windows 窗体和控制台应用程序。

### <a name="components-included-by-this-workload"></a>此工作负载所包含的组件

组件 ID | 名称 | 依赖项类型
--- | --- | ---
Microsoft.Component.ClickOnce | ClickOnce 发布 | 必需
Microsoft.Component.MSBuild | MSBuild | 必需
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 必需
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目标包 | 必需
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET framework 4.6.1 开发工具 | 必需
Microsoft.VisualStudio.Component.Debugger.JustInTime | 实时调试器 | 必需
Microsoft.VisualStudio.Component.ManagedDesktop.Core | 托管桌面工作负载核心 | 必需
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | .NET 桌面开发工具 | 必需
Microsoft.VisualStudio.Component.PortableLibrary | .NET 可移植库目标包 | 必需
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 和 Visual Basic Roslyn 编译器 | 必需
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 必需
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 数据类型 | 必需
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 静态分析工具 | 必需
Microsoft.VisualStudio.Component.TextTemplating | 文本模板转换 | 必需
Microsoft.VisualStudio.Component.VisualStudioData | 数据源和服务引用 | 必需
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 建议
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 目标包 | 建议
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目标包 | 建议
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目标包 | 建议
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目标包 | 建议
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目标包 | 建议
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 开发工具 | 建议
Microsoft.VisualStudio.Component.DiagnosticTools | 分析工具 | 建议
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 工具 | 建议
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 建议
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 建议
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 目标包 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 开发工具 | Optional
Microsoft.Net.Core.Component.SDK | .NET Core 1.0.1 开发工具 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools | .NET Core 1.0 - 1.1 开发工具 | Optional
Microsoft.VisualStudio.Component.CodeClone | 代码克隆 | Optional
Microsoft.VisualStudio.Component.CodeMap | 代码图 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | 实时依赖项验证 | Optional
Microsoft.VisualStudio.Component.FSharp | F# 语言支持 | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML 编辑器 | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Optional
Microsoft.VisualStudio.Component.NuGet | NuGet 程序包管理器 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | Optional
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | 体系结构和分析工具 | Optional


## <a name="game-development-with-unity"></a>使用 Unity 的游戏开发

**ID：**Microsoft.VisualStudio.Workload.ManagedGame

**说明：**使用 Unity（功能强大的跨平台开发环境）创建 2D 和 3D 游戏。

### <a name="components-included-by-this-workload"></a>此工作负载所包含的组件

组件 ID | 名称 | 依赖项类型
--- | --- | ---
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 和 Visual Basic Roslyn 编译器 | 必需
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 必需
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 静态分析工具 | 必需
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools for Unity | 必需
Component.UnityEngine | Unity 编辑器 | 建议


## <a name="linux-development-with-c"></a>使用 C++ 的 Linux 开发

**ID：**Microsoft.VisualStudio.Workload.NativeCrossPlat

**说明：**创建和调试在 Linux 环境中运行的应用程序。

### <a name="components-included-by-this-workload"></a>此工作负载所包含的组件

组件 ID | 名称 | 依赖项类型
--- | --- | ---
Component.MDD.Linux | 适用于 Linux 开发的 Visual C++ | 必需
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ 核心功能 | 必需
Microsoft.VisualStudio.Component.Windows10SDK | Windows 通用 C 运行时 | 必需


## <a name="desktop-development-with-c"></a>使用 C++ 的桌面开发

**ID：**Microsoft.VisualStudio.Workload.NativeDesktop

**说明：**使用功能强大的 Visual C++ 工具集、ATL 以及 MFC 和 C++/CLI 等可选功能生成基于 Windows 的经典应用程序。

### <a name="components-included-by-this-workload"></a>此工作负载所包含的组件

组件 ID | 名称 | 依赖项类型
--- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 必需
Microsoft.VisualStudio.Component.ClassDesigner | 类设计器 | 必需
Microsoft.VisualStudio.Component.CodeMap | 代码图 | 必需
Microsoft.VisualStudio.Component.Debugger.JustInTime | 实时调试器 | 必需
Microsoft.VisualStudio.Component.GraphDocument | DGML 编辑器 | 必需
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 和 Visual Basic Roslyn 编译器 | 必需
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 必需
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 必需
Microsoft.VisualStudio.Component.TextTemplating | 文本模板转换 | 必需
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ 核心功能 | 必需
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | 适用于 C++ 的体系结构工具 | 必需
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Visual C++ 核心桌面功能 | 必需
Microsoft.VisualStudio.Component.Graphics.Tools | 适用于 DirectX 的图形调试器和 GPU 探查器 | 建议
Microsoft.VisualStudio.Component.Graphics.Win81 | 图形工具 Windows 8.1 SDK | 建议
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 静态分析工具 | 建议
Microsoft.VisualStudio.Component.VC.CMake.Project | 适用于 CMake 的 Visual C++ 工具 | 建议
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ 分析工具 | 建议
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141 工具集（x86、x64） | 建议
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 建议
Component.Incredibuild | IncrediBuild | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Windows 通用 CRT SDK | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目标包 | Optional
Microsoft.VisualStudio.Component.VC.140 | VC++ 2015.3 v140 工具集（x86、x64） | Optional
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL 支持 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC 和 ATL 支持（x86 和 x64） | Optional
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2（实验） | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | C++/CLI 支持 | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | 标准库模块 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | Optional
Microsoft.VisualStudio.Component.WinXP | 针对 C++ 的 Windows XP 支持 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK 和 UCRT SDK | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | 针对 C++ 的 Windows XP 支持 | Optional


## <a name="game-development-with-c"></a>使用 C++ 的游戏开发

**ID：**Microsoft.VisualStudio.Workload.NativeGame

**说明：**以 DirectX、Unreal 或 Cocos2d 为后盾，利用 C++ 的强大功能生成专业游戏。

### <a name="components-included-by-this-workload"></a>此工作负载所包含的组件

组件 ID | 名称 | 依赖项类型
--- | --- | ---
Microsoft.VisualStudio.Component.Windows10SDK | Windows 通用 C 运行时 | 必需
Microsoft.VisualStudio.Component.Graphics.Tools | 适用于 DirectX 的图形调试器和 GPU 探查器 | 建议
Microsoft.VisualStudio.Component.Graphics.Win81 | 图形工具 Windows 8.1 SDK | 建议
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 静态分析工具 | 建议
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ 核心功能 | 建议
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ 分析工具 | 建议
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141 工具集（x86、x64） | 建议
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 建议
Component.Cocos | Cocos | Optional
Component.Incredibuild | IncrediBuild | Optional
Component.Unreal | Unreal 引擎安装程序 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Windows 通用 CRT SDK | Optional
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 目标包 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目标包 | Optional
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目标包 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目标包 | Optional
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目标包 | Optional
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目标包 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET framework 4.6.1 开发工具 | Optional
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 开发工具 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 和 Visual Basic Roslyn 编译器 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK 和 UCRT SDK | Optional


## <a name="mobile-development-with-c"></a>使用 C++ 的移动开发

**ID：**Microsoft.VisualStudio.Workload.NativeMobile

**说明：**使用 C++ 生成适用于 iOS、Android 或 Windows 的跨平台应用程序。

### <a name="components-included-by-this-workload"></a>此工作负载所包含的组件

组件 ID | 名称 | 依赖项类型
--- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ 核心功能 | 必需
Component.Android.NDK.R13B | Android NDK (R13B) | 建议
Component.Android.SDK19 | Android SDK 安装程序（API 级别 19 和 21） | 建议
Component.Android.SDK22 | Android SDK 安装程序（API 级别 22） | 建议
Component.Ant | Apache Ant (1.9.3) | 建议
Component.MDD.Android | C++ Android 开发工具 | 建议
Component.Android.Emulator | 适用于 Android 的 Visual Studio 仿真程序 | Optional
Component.Android.NDK.R11C | Android NDK (R11C) | Optional
Component.Android.NDK.R11C_3264 | Android NDK (R11C)（32 位） | Optional
Component.Android.NDK.R12B | Android NDK (R12B) | Optional
Component.Android.NDK.R12B_3264 | Android NDK (R12B)（32 位） | Optional
Component.Android.NDK.R13B_3264 | Android NDK (R13B)（32 位） | Optional
Component.Android.SDK23 | Android SDK 安装程序（API 级别 23） | Optional
Component.Google.Android.Emulator.API23.V2 | Google Android 仿真程序（API 级别 23） | Optional
Component.HAXM | Intel 硬件加速执行管理器 (HAXM) | Optional
Component.Incredibuild | IncrediBuild | Optional
Component.JavaJDK | Java SE 开发工具包 (8.0.920.14) | Optional
Component.MDD.IOS | C++ iOS 开发工具 | Optional


## <a name="net-core-cross-platform-development"></a>.NET Core 跨平台开发

**ID：**Microsoft.VisualStudio.Workload.NetCoreTools

**说明：**使用 .NET Core、ASP.NET Core、HTML、JavaScript 和 CSS 生成跨平台应用程序

### <a name="components-included-by-this-workload"></a>此工作负载所包含的组件

组件 ID | 名称 | 依赖项类型
--- | --- | ---
Component.WebSocket | WebSocket4Net | 必需
Microsoft.Component.ClickOnce | ClickOnce 发布 | 必需
Microsoft.Component.MSBuild | MSBuild | 必需
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目标包 | 必需
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目标包 | 必需
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 必需
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目标包 | 必需
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET framework 4.6.1 开发工具 | 必需
Microsoft.Net.Core.Component.SDK | .NET Core 1.0.1 开发工具 | 必需
Microsoft.NetCore.ComponentGroup.Web | .NET Core 1.0 - 1.1 开发工具 | 必需
Microsoft.VisualStudio.Component.AppInsights.Tools | 开发人员分析工具 | 必需
Microsoft.VisualStudio.Component.Common.Azure.Tools | 连接和发布工具 | 必需
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 必需
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 诊断 | 必需
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 和 TypeScript 语言支持 | 必需
Microsoft.VisualStudio.Component.ManagedDesktop.Core | 托管桌面工作负载核心 | 必需
Microsoft.VisualStudio.Component.NuGet | NuGet 程序包管理器 | 必需
Microsoft.VisualStudio.Component.PortableLibrary | .NET 可移植库目标包 | 必需
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 和 Visual Basic Roslyn 编译器 | 必需
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 必需
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 运行时 | 必需
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 数据类型 | 必需
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server 命令行实用工具 | 必需
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 支持的数据源 | 必需
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 必需
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 必需
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 必需
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 静态分析工具 | 必需
Microsoft.VisualStudio.Component.TextTemplating | 文本模板转换 | 必需
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 必需
Microsoft.VisualStudio.Component.VisualStudioData | 数据源和服务引用 | 必需
Microsoft.VisualStudio.Component.Web | ASP.NET 和 Web 开发工具 | 必需
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 必需
Microsoft.VisualStudio.Component.DockerTools | 容器开发工具 | 建议


## <a name="mobile-development-with-net"></a>使用 .NET 的移动开发

**ID：**Microsoft.VisualStudio.Workload.NetCrossPlat

**说明：**使用 Xmarin 生成适用于 iOS、Android 或 Windows 的跨平台应用程序。

### <a name="components-included-by-this-workload"></a>此工作负载所包含的组件

组件 ID | 名称 | 依赖项类型
--- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 必需
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目标包 | 必需
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET framework 4.6.1 开发工具 | 必需
Microsoft.VisualStudio.Component.PortableLibrary | .NET 可移植库目标包 | 必需
Component.Android.NDK.R13B | Android NDK (R13B) | 建议
Component.Android.SDK23 | Android SDK 安装程序（API 级别 23） | 建议
Component.Google.Android.Emulator.API23.V2 | Google Android 仿真程序（API 级别 23） | 建议
Component.HAXM | Intel 硬件加速执行管理器 (HAXM) | 建议
Component.JavaJDK | Java SE 开发工具包 (8.0.920.14) | 建议
Component.Xamarin | Xamarin | 建议
Component.Xamarin.Inspector | Xamarin Workbooks | 建议
Component.Xamarin.Profiler | Xamarin Profiler | 建议
Component.Xamarin.RemotedSimulator | Xamarin 远程模拟器 | 建议
Microsoft.VisualStudio.Component.FSharp | F# 语言支持 | 建议
Microsoft.VisualStudio.Component.NuGet | NuGet 程序包管理器 | 建议
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 和 Visual Basic Roslyn 编译器 | 建议
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 建议
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 静态分析工具 | 建议
Microsoft.Component.ClickOnce | ClickOnce 发布 | Optional
Microsoft.Component.NetFX.Native | .NET Native | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | 开发人员分析工具 | Optional
Microsoft.VisualStudio.Component.CodeClone | 代码克隆 | Optional
Microsoft.VisualStudio.Component.CodeMap | 代码图 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | 实时依赖项验证 | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | 分析工具 | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML 编辑器 | Optional
Microsoft.VisualStudio.Component.Graphics | 图像和 3D 模型编辑器 | Optional
Microsoft.VisualStudio.Component.Phone.Emulator | Windows 10 移动版仿真程序（周年纪念版） | Optional
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 数据类型 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Optional
Microsoft.VisualStudio.Component.VisualStudioData | 数据源和服务引用 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | 体系结构和分析工具 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | 适用于 Xamarin 的通用 Windows 平台工具 (2.0) | Optional


## <a name="aspnet-and-web-development"></a>ASP.NET 和 Web 开发

**ID：**Microsoft.VisualStudio.Workload.NetWeb

**说明：**使用 ASP.NET、ASP.NET Core、HTML、JavaScript 和 CSS 生成 Web 应用程序。

### <a name="components-included-by-this-workload"></a>此工作负载所包含的组件

组件 ID | 名称 | 依赖项类型
--- | --- | ---
Component.WebSocket | WebSocket4Net | 必需
Microsoft.Component.ClickOnce | ClickOnce 发布 | 必需
Microsoft.Component.MSBuild | MSBuild | 必需
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目标包 | 必需
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目标包 | 必需
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 必需
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目标包 | 必需
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET framework 4.6.1 开发工具 | 必需
Microsoft.Net.Core.Component.SDK | .NET Core 1.0.1 开发工具 | 必需
Microsoft.NetCore.ComponentGroup.Web | .NET Core 1.0 - 1.1 开发工具 | 必需
Microsoft.VisualStudio.Component.AppInsights.Tools | 开发人员分析工具 | 必需
Microsoft.VisualStudio.Component.Common.Azure.Tools | 连接和发布工具 | 必需
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 必需
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 诊断 | 必需
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 和 TypeScript 语言支持 | 必需
Microsoft.VisualStudio.Component.ManagedDesktop.Core | 托管桌面工作负载核心 | 必需
Microsoft.VisualStudio.Component.NuGet | NuGet 程序包管理器 | 必需
Microsoft.VisualStudio.Component.PortableLibrary | .NET 可移植库目标包 | 必需
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 和 Visual Basic Roslyn 编译器 | 必需
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 必需
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 运行时 | 必需
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 数据类型 | 必需
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server 命令行实用工具 | 必需
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 支持的数据源 | 必需
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 必需
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 必需
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 必需
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 静态分析工具 | 必需
Microsoft.VisualStudio.Component.TextTemplating | 文本模板转换 | 必需
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 必需
Microsoft.VisualStudio.Component.VisualStudioData | 数据源和服务引用 | 必需
Microsoft.VisualStudio.Component.Web | ASP.NET 和 Web 开发工具 | 必需
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 必需
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 目标包 | 建议
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目标包 | 建议
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目标包 | 建议
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 开发工具 | 建议
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 建议
Microsoft.VisualStudio.Component.DiagnosticTools | 分析工具 | 建议
Microsoft.VisualStudio.Component.DockerTools | 容器开发工具 | 建议
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 工具 | 建议
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 建议
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 建议
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 建议
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 目标包 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 开发工具 | Optional
Microsoft.VisualStudio.Component.ClassDesigner | 类设计器 | Optional
Microsoft.VisualStudio.Component.CodeClone | 代码克隆 | Optional
Microsoft.VisualStudio.Component.CodeMap | 代码图 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | 实时依赖项验证 | Optional
Microsoft.VisualStudio.Component.FSharp | F# 语言支持 | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML 编辑器 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | 体系结构和分析工具 | Optional
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | Optional


## <a name="nodejs-development"></a>Node.js 开发

**ID：**Microsoft.VisualStudio.Workload.Node

**说明：**使用 Node.js（事件驱动的异步 JavaScript 运行时）生成可扩展的网络应用程序。

### <a name="components-included-by-this-workload"></a>此工作负载所包含的组件

组件 ID | 名称 | 依赖项类型
--- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 和 TypeScript 语言支持 | 必需
Microsoft.VisualStudio.Component.Node.Tools | Node.js 支持 | 必需
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 必需
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 必需
Microsoft.VisualStudio.Component.Common.Azure.Tools | 连接和发布工具 | 建议
Microsoft.VisualStudio.Component.Git | 用于 Windows 的 Git | 建议
Component.WebSocket | WebSocket4Net | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | 开发人员分析工具 | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | 分析工具 | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 诊断 | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 静态分析工具 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ 核心功能 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141 工具集（x86、x64） | Optional


## <a name="officesharepoint-development"></a>Office/SharePoint 开发

**ID：**Microsoft.VisualStudio.Workload.Office

**说明：**使用 C#、VB 和 JavaScript 创建 Office 和 SharePoint 外接程序、SharePoint 解决方案和 VSTO 外接程序。

### <a name="components-included-by-this-workload"></a>此工作负载所包含的组件

组件 ID | 名称 | 依赖项类型
--- | --- | ---
Component.WebSocket | WebSocket4Net | 必需
Microsoft.Component.ClickOnce | ClickOnce 发布 | 必需
Microsoft.Component.MSBuild | MSBuild | 必需
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目标包 | 必需
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目标包 | 必需
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 必需
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目标包 | 必需
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目标包 | 必需
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET framework 4.6.1 开发工具 | 必需
Microsoft.VisualStudio.Component.AppInsights.Tools | 开发人员分析工具 | 必需
Microsoft.VisualStudio.Component.Common.Azure.Tools | 连接和发布工具 | 必需
Microsoft.VisualStudio.Component.Debugger.JustInTime | 实时调试器 | 必需
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 必需
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 诊断 | 必需
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 和 TypeScript 语言支持 | 必需
Microsoft.VisualStudio.Component.ManagedDesktop.Core | 托管桌面工作负载核心 | 必需
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | .NET 桌面开发工具 | 必需
Microsoft.VisualStudio.Component.NuGet | NuGet 程序包管理器 | 必需
Microsoft.VisualStudio.Component.PortableLibrary | .NET 可移植库目标包 | 必需
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 和 Visual Basic Roslyn 编译器 | 必需
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 必需
Microsoft.VisualStudio.Component.Sharepoint.Tools | Visual Studio 的 Office 开发工具 | 必需
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 运行时 | 必需
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 数据类型 | 必需
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server 命令行实用工具 | 必需
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 支持的数据源 | 必需
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 必需
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 必需
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 必需
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 静态分析工具 | 必需
Microsoft.VisualStudio.Component.TextTemplating | 文本模板转换 | 必需
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 必需
Microsoft.VisualStudio.Component.VisualStudioData | 数据源和服务引用 | 必需
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 必需
Microsoft.VisualStudio.Component.Web | ASP.NET 和 Web 开发工具 | 必需
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 必需
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 必需
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools for Office (VSTO) | 建议
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Optional


## <a name="universal-windows-platform-development"></a>通用 Windows 平台开发

**ID：**Microsoft.VisualStudio.Workload.Universal

**说明：**使用 C#、VB 和 JavaScript 或 C++（可选）创建适用于通用 Windows 平台的应用程序。

### <a name="components-included-by-this-workload"></a>此工作负载所包含的组件

组件 ID | 名称 | 依赖项类型
--- | --- | ---
Component.WebSocket | WebSocket4Net | 必需
Microsoft.Component.ClickOnce | ClickOnce 发布 | 必需
Microsoft.Component.NetFX.Native | .NET Native | 必需
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 必需
Microsoft.VisualStudio.Component.AppInsights.Tools | 开发人员分析工具 | 必需
Microsoft.VisualStudio.Component.DiagnosticTools | 分析工具 | 必需
Microsoft.VisualStudio.Component.Graphics | 图像和 3D 模型编辑器 | 必需
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 诊断 | 必需
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 和 TypeScript 语言支持 | 必需
Microsoft.VisualStudio.Component.NuGet | NuGet 程序包管理器 | 必需
Microsoft.VisualStudio.Component.PortableLibrary | .NET 可移植库目标包 | 必需
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 和 Visual Basic Roslyn 编译器 | 必需
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 必需
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 数据类型 | 必需
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 静态分析工具 | 必需
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 必需
Microsoft.VisualStudio.Component.UWP.Support | 通用 Windows 平台工具 (2.0) | 必需
Microsoft.VisualStudio.Component.VisualStudioData | 数据源和服务引用 | 必需
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 必需
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | 适用于 Cordova 的通用 Windows 平台工具 (2.0) | 必需
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | 适用于 Xamarin 的通用 Windows 平台工具 (2.0) | 必需
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 建议
Microsoft.Component.VC.Runtime.OSSupport | 适用于 UWP 的 Visual C++ 运行时 | Optional
Microsoft.VisualStudio.Component.CodeClone | 代码克隆 | Optional
Microsoft.VisualStudio.Component.CodeMap | 代码图 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | 实时依赖项验证 | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML 编辑器 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | 适用于 DirectX 的图形调试器和 GPU 探查器 | Optional
Microsoft.VisualStudio.Component.Graphics.Win81 | 图形工具 Windows 8.1 SDK | Optional
Microsoft.VisualStudio.Component.Phone.Emulator | Windows 10 移动版仿真程序（周年纪念版） | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ 核心功能 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM | 用于 ARM 的 Visual C++ 编译器和库 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141 工具集（x86、x64） | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | 体系结构和分析工具 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.VC | C++ 通用 Windows 平台工具 | Optional


## <a name="visual-studio-extension-development"></a>Visual Studio 扩展开发

**ID：**Microsoft.VisualStudio.Workload.VisualStudioExtension

**说明：**创建适用于 Visual Studio 的加载项和扩展，包括新命令、代码分析器和工具窗口。

### <a name="components-included-by-this-workload"></a>此工作负载所包含的组件

组件 ID | 名称 | 依赖项类型
--- | --- | ---
Microsoft.Component.ClickOnce | ClickOnce 发布 | 必需
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 必需
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目标包 | 必需
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET framework 4.6.1 开发工具 | 必需
Microsoft.VisualStudio.Component.NuGet | NuGet 程序包管理器 | 必需
Microsoft.VisualStudio.Component.PortableLibrary | .NET 可移植库目标包 | 必需
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Visual Studio 扩展开发必备组件 | 必需
Microsoft.VisualStudio.Component.CodeClone | 代码克隆 | 建议
Microsoft.VisualStudio.Component.CodeMap | 代码图 | 建议
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | 实时依赖项验证 | 建议
Microsoft.VisualStudio.Component.DiagnosticTools | 分析工具 | 建议
Microsoft.VisualStudio.Component.GraphDocument | DGML 编辑器 | 建议
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 建议
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 建议
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 建议
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | 体系结构和分析工具 | 建议
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | Optional
Microsoft.Component.MSBuild | MSBuild | Optional
Microsoft.Component.VC.Runtime.OSSupport | 适用于 UWP 的 Visual C++ 运行时 | Optional
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目标包 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | 开发人员分析工具 | Optional
Microsoft.VisualStudio.Component.ClassDesigner | 类设计器 | Optional
Microsoft.VisualStudio.Component.DslTools | 建模 SDK | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 和 Visual Basic Roslyn 编译器 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 静态分析工具 | Optional
Microsoft.VisualStudio.Component.TextTemplating | 文本模板转换 | Optional
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL 支持 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC 和 ATL 支持（x86 和 x64） | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ 核心功能 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141 工具集（x86、x64） | Optional
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | Optional


## <a name="mobile-development-with-javascript"></a>使用 JavaScript 的移动开发

**ID：**Microsoft.VisualStudio.Workload.WebCrossPlat

**说明：**使用用于 Apache Cordova 的工具生成 Android、iOS 和 UWP 应用。

### <a name="components-included-by-this-workload"></a>此工作负载所包含的组件

组件 ID | 名称 | 依赖项类型
--- | --- | ---
Component.CordovaToolset.6.3.1 | Cordova 6.3.1 工具集 | 必需
Component.WebSocket | WebSocket4Net | 必需
Microsoft.VisualStudio.Component.Cordova | 使用 JavaScript 核心功能的移动开发 | 必需
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 诊断 | 必需
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 和 TypeScript 语言支持 | 必需
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 必需
Component.Android.SDK23 | Android SDK 安装程序（API 级别 23） | Optional
Component.Google.Android.Emulator.API23.V2 | Google Android 仿真程序（API 级别 23） | Optional
Component.HAXM | Intel 硬件加速执行管理器 (HAXM) | Optional
Component.JavaJDK | Java SE 开发工具包 (8.0.920.14) | Optional
Microsoft.Component.ClickOnce | ClickOnce 发布 | Optional
Microsoft.Component.NetFX.Native | .NET Native | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | 开发人员分析工具 | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | 分析工具 | Optional
Microsoft.VisualStudio.Component.Git | 用于 Windows 的 Git | Optional
Microsoft.VisualStudio.Component.Graphics | 图像和 3D 模型编辑器 | Optional
Microsoft.VisualStudio.Component.Phone.Emulator | Windows 10 移动版仿真程序（周年纪念版） | Optional
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 数据类型 | Optional
Microsoft.VisualStudio.Component.VisualStudioData | 数据源和服务引用 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | 适用于 Cordova 的通用 Windows 平台工具 (2.0) | Optional

## <a name="unaffiliated-components"></a>独立组件

这些组件不随附于任何工作负载，但可选择作为单个组件。

组件 ID | 名称
--- | ---
Component.GitHub.VisualStudio | 适用于 Visual Studio 的 GitHub 扩展
Microsoft.Component.Blend.SDK.WPF | 用于 .NET 的 Blend for Visual Studio SDK
Microsoft.Component.HelpViewer | 帮助查看器
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5 开发工具
Microsoft.VisualStudio.Component.DependencyValidation.Community | 依赖项验证
Microsoft.VisualStudio.Component.LinqToSql | LINQ to SQL 工具
Microsoft.VisualStudio.Component.TestTools.Core | 测试工具核心功能
Microsoft.VisualStudio.Component.TypeScript.2.0 | TypeScript 2.0 SDK

## <a name="see-also"></a>另请参阅

* [Visual Studio 工作负荷和组件 ID](workload-and-component-ids.md)
* [Visual Studio 管理员指南](visual-studio-administrator-guide.md)
* [使用命令行参数安装 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [创建 Visual Studio 的脱机安装](create-an-offline-installation-of-visual-studio.md)

